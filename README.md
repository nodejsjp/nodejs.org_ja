# Node.js公式ドキュメント翻訳サイト

このリポジトリは、Node.js日本ユーザグループにる、Node.js公式ドキュメントの翻訳サイト公開用リポジトリです。

## 関連リポジトリ

* [nodejsjp/nodejsjp.github.com](https://github.com/nodejsjp/nodejsjp.github.com): Node.js日本ユーザグループ公式サイト
  * [Node.js日本ユーザグループ](http://nodejs.jp/)のトップページなど、翻訳ドキュメント以外のコンテンツ用リポジトリです。
* [nodejsjp/nodejs.org_ja](https://github.com/nodejsjp/nodejs.org_ja): Node.js公式ドキュメントの翻訳サイト
  * このリポジトリです。
* [nodejsjp/node](https://github.com/koichik/node): 翻訳ドキュメントのソース
  * Node.js公式ドキュメントを翻訳したソース用のリポジトリです。

公式ドキュメントの翻訳は`nodejsjp/node`上のmarkdownに対して行い、ビルドされたHTMLを`nodejsjp/nodejs.org_ja` (このリポジトリ) にコミットすることで公開しています。このリポジトリ上のHTMLを直接編集することはしません。

## 翻訳手順

### ソースドキュメントの修正

* `joyent/node`をクローンする。
* `nodejsjp/node`をリモートに追加する

```sh
$ git remote add nodejsjp https://github.com/nodejsjp/nodejsjp.github.com.git
```

* `nodejsjp/node`をフェッチする

```sh
$ git fetch nodejsjp
```

* 翻訳用ブランチをチェックアウトする
  * 本家リポジトリの`master`に対応するブランチは`japanese`です。
  * 本家リポジトリの`v0.xx`ブランチに対応するのは`japanese-v0.xx`です。

```sh
$ git checkout -b japanese nodejsjp/japanese
```

* 原文の変更をマージする
  * 新バージョンに対応する場合のみ必要です。誤字や誤訳を修正する場合は不要です。
  * コンフリクトしなくても多くの場合は翻訳を修正する必要があるため、`--no-commit`を指定します。

```sh
$ git merge --no-ff --no-commit v0.xx.yy
```

* `doc`以下のドキュメントを編集する。
* ドキュメントをビルドする

```sh
$ ./configure
$ make doc
```

* ブラウザで編集内容を確認してコミットし、自分のリモートリポジトリにプッシュする。
* `nodejsjp/node`にプルリクエストする。

### 翻訳サイトの修正

* `nodejsjp/nodejs.org_ja`をクローンする。
* 「翻訳ソースの修正」でビルドしたHTMLファイルをコピーする
  * 本家リポジトリの`master`に対応するドキュメントはルート直下にコピーします。
  * 本家リポジトリの`v0.xx`ブランチに対応するドキュメントは
    `docs/v0.xx/`以下にコピーします。

```sh
cp -R path/to/node/out/doc/* ./
```

* コミットして自分のリモートリポジトリにプッシュする。
* `nodejsjp/nodejs.org_ja`にプルリクエストする。

### 公式サイトの修正

* `nodejsjp/nodejsjp.github.com`をクローンする。
* ドキュメントを修正する。
* コミットして自分のリモートリポジトリにプッシュする。
* `nodejsjp/nodejsjp.github.com`にプルリクエストする。

