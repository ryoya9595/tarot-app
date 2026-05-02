# パーソナル・タロット — 運用メモ

> このフォルダの中身を後から開いた時用のメモ。リンクや更新手順をまとめてある。
> ※ 同じ「占い」テーマで先輩の `/Users/ryoya/Desktop/AI Agents/占い/`（月夜のタロット）もあり。両方並走中。

## 🔗 公開URL・リポジトリ

- **公開サイト**: https://ryoya9595.github.io/tarot-app/
- **GitHubリポジトリ**: https://github.com/ryoya9595/tarot-app
- **公開状態**: Public（GitHub Pages無料枠を使うため）
- **デプロイ方式**: GitHub Pages（mainブランチのルート）

## 🚀 公開した日

2026-05-02（Claude Code経由で初回デプロイ）

## 📝 修正・更新したい時

このフォルダ（`/Users/ryoya/Desktop/AI Agents/tarot-app/`）でファイル編集 → コミット&プッシュ。

```sh
cd "/Users/ryoya/Desktop/AI Agents/tarot-app"
git add .
git commit -m "更新内容のメモ"
git push
```

→ プッシュから30秒〜1分で公開サイトに反映される。

## 💻 ローカルで動作確認

```sh
# 一番ラクな方法：ダブルクリックで開く
open "/Users/ryoya/Desktop/AI Agents/tarot-app/index.html"
```

外部CDN一切使ってないので `file://` でも普通に動く。

## 📁 ファイル構成

| ファイル | 役割 |
|---|---|
| `index.html` | 全部入りの単一HTML（CSS・JS埋め込み） |
| `README.md` | リポジトリのトップページ用 |
| `MEMO.md` | このメモ（運用情報） |

## 🌟 月夜のタロットとの違い

| | 月夜のタロット | パーソナル・タロット（こっち） |
|---|---|---|
| 作り方 | Claude Designで生成 → ZIP展開 | Claude Codeで一気に書いた |
| 構成 | React + Babel（CDN）の複数ファイル | バニラJSの単一HTML |
| 入力 | テーマ選択のみ | 名前・生年月日・悩み・テーマ |
| 結果 | カード解釈 | 解釈 + ライフパスナンバー連動 |
| 引き方 | 自動シャッフル | 22枚から直感で3枚選ぶ |

## ⚠️ 注意点

- **永続化なし**: 履歴は保存しない（リロードでリセット）。月夜のタロットはlocalStorageで履歴30件保存してる
- **解釈テキスト**: ハードコード（`CARDS` 配列に直書き）。テーマごとに `love` / `work` / `general` の3種類

## 🔧 こんな時はこうする

### カードの解釈文を編集したい
`index.html` の `CARDS` 配列の該当カードの `love` / `work` / `general` を書き換える。

### 新しいテーマ（例: 金運）を追加したい
1. `THEMES` オブジェクトに追加
2. `CARDS` 配列の22枚それぞれに新キー追加
3. `SYNTHESIS` オブジェクトに新テーマの総合メッセージ関数を追加
4. 入力フォームのラジオボタンに選択肢追加

### サイトを非公開にしたい
リポジトリ Settings → Pages → Source を「None」に変更。

## 🧙 元のアイデア・由来

明日のセミナー用に「Claude Designで何が作れるか」の話のネタとして、
Claude Codeで30分くらいで作った → そのままGitHub公開。
受講生に「自分にもできるかも」と思わせるための実演用デモ。
