+++
title = '使用 Hugo 與 GitHub 建立個人博客的完整指南'
date = 2023-12-26T05:20:15+08:00
+++

這是我關於如何使用 Hugo 和 GitHub 建立和部署靜態博客的教學，參考了這個非常有用的 [YouTube 影片](https://www.youtube.com/watch?v=LIFvgrRxdt4&t=2s)。身為台大電機系的學生，我發現這個過程既有趣又富有教育意義。以下是我按步驟整理的內容：

## 建立 Hugo 博客

### 建立兩個 GitHub 儲存庫

首先，我們需要在 GitHub 上建立兩個儲存庫：

1. **源代碼儲存庫**（例如 `blog`）用於存放 Hugo 的源代碼和博文。
2. **靜態內容儲存庫**（例如 `username.github.io`），用於存放 Hugo 生成的靜態網站內容。

### 在本地建立 Hugo 網站

接下來，我們在本地電腦上複製第一個儲存庫，並建立一個新的 Hugo 網站：

```bash
git clone https://github.com/yourusername/blog.git
cd blog
hugo new site insightbotics-blog
```

### 選擇並添加 Hugo 主題

我在 Hugo 的官方主題庫中挑選了一個稱為 Mainroad 的主題，並將其作為子模組添加到我的 Hugo 網站中：

```bash
cd insightbotics-blog
cd themes
git submodule add https://github.com/vimux/mainroad.git
```

### 配置 Hugo 網站

編輯 `config.toml` 文件，設置主題和網站的其他相關配置。

### 建立和預覽內容

添加新的博文並在本地預覽網站：

```bash
hugo new posts/your-post-name.md
hugo server
```

## 部署 Hugo 博客

### 將靜態內容儲存庫添加為子模組

我們需要將第二個儲存庫作為子模組添加到 `public` 目錄下，這個目錄是 Hugo 生成靜態文件的地方：

```bash
git submodule add -b main git@github.com:yourusername/yourusername.github.io.git public
```

### 生成靜態網站並推送到 GitHub

運行 Hugo 來生成靜態內容，然後將其推送到靜態內容儲存庫：

```bash
hugo -t mainroad
cd public
git add .
git commit -m "Initial commit"
git push origin main
```

### 在 GitHub Pages 啟用網站部署

在 GitHub 上的靜態內容儲存庫的設置中，確保從 `main` 分支部署網站。

## 結語

按照這些步驟，您就可以輕鬆地在 GitHub 上部署自己的 Hugo 博客了。這個過程不僅簡單，而且可以讓您完全控制自己的內容和網站的外觀。希望這篇教學對您有所幫助！

祝您博客建設愉快！

