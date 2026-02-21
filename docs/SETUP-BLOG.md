# ブログ機能構築ガイド

## 概要

シンプルなブログ・日記機能を構築する。デザインは最小限にとどめ、後から拡張しやすい構成にする。

---

## Step 1: パッケージのインストール

Cursorのターミナルで、プロジェクトルート（`yusahal-site/`）にて以下を実行：

```bash
# React インテグレーション
npx astro add react

# Tailwind CSS インテグレーション
npx astro add tailwind
```

それぞれ「Y」で進める。`astro.config.mjs` と `tailwind.config.mjs` が自動更新される。

---

## Step 2: ファイルの配置

以下のファイルをプロジェクトに追加する（このガイドと同梱のファイルをコピー）。

```
src/
├── content.config.ts          ← Content Collections 定義
├── content/
│   └── blog/
│       └── 2026-02-20-hello.md   ← サンプル記事
├── styles/
│   └── global.css             ← Tailwind + グローバルスタイル
├── layouts/
│   ├── BaseLayout.astro       ← 全ページ共通レイアウト
│   └── BlogPost.astro         ← ブログ記事用レイアウト
├── components/
│   ├── Header.astro           ← ナビゲーション
│   └── Footer.astro           ← フッター
├── pages/
│   ├── index.astro            ← トップページ（更新）
│   └── blog/
│       ├── index.astro        ← ブログ一覧
│       └── [...slug].astro    ← 個別記事ページ
```

---

## Step 3: 動作確認

```bash
npm run dev
```

以下のページを確認：
- `http://localhost:4321/` → トップページ
- `http://localhost:4321/blog/` → ブログ一覧
- `http://localhost:4321/blog/2026-02-20-hello/` → サンプル記事

---

## Step 4: デプロイ

```bash
git add .
git commit -m "feat: ブログ機能追加"
git push
```

Cloudflare Pages が自動でビルド＆デプロイ → `yusahal.com` に反映。

---

## 記事の追加方法

`src/content/blog/` に Markdown ファイルを追加するだけ：

```markdown
---
title: "記事タイトル"
description: "記事の説明"
pubDate: 2026-02-21
tags: ["日記", "開発"]
---

ここに本文を書く。
```

ファイル名は `YYYY-MM-DD-slug.md` の形式を推奨（任意）。

---

## 今後の拡張ポイント

- タグ別一覧ページ（`/blog/tags/[tag].astro`）
- ページネーション（記事数が増えたら）
- RSS フィード（`@astrojs/rss`）
- OGP / SNSシェア対応
- 検索機能
- トップページのデザイン強化（VTuber的演出）
