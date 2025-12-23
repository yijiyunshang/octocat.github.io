# 问卷星应用 - 零成本部署指南

## 应用特点分析

本问卷应用是一个**纯前端应用**，具有以下特点：
- 使用 HTML、CSS、JavaScript 构建
- 数据存储在浏览器的 localStorage 中
- 无需后端服务器
- 支持离线使用
- 适合静态网站托管

## 零成本部署方案

### 方案1：GitHub Pages（推荐）

**优势：**
- 完全免费
- 无限流量
- 支持自定义域名
- 自动 HTTPS
- 与 GitHub 代码仓库完美集成

**部署步骤：**

1. **创建 GitHub 账号**
   - 访问 [GitHub](https://github.com) 注册免费账号

2. **创建新仓库**
   - 点击 "New repository"
   - 仓库名称：`questionnaire-app`
   - 选择 "Public"（公开仓库）
   - 勾选 "Add a README file"
   - 点击 "Create repository"

3. **上传项目文件**
   - 进入新建的仓库
   - 点击 "Add file" → "Upload files"
   - 拖拽 `index.html` 文件到上传区域
   - 填写提交信息，点击 "Commit changes"

4. **启用 GitHub Pages**
   - 进入仓库的 "Settings" 页面
   - 点击左侧菜单的 "Pages"
   - 在 "Build and deployment" 部分：
     - Source: 选择 "Deploy from a branch"
     - Branch: 选择 "main"，点击 "Save"
   - 等待几分钟，GitHub Pages 会自动部署你的应用
   - 部署完成后会显示访问链接（如：`https://yourusername.github.io/questionnaire-app`）

### 方案2：Netlify

**优势：**
- 完全免费
- 自动部署（连接 GitHub 仓库）
- 支持自定义域名
- 自动 HTTPS
- 提供 CDN 加速

**部署步骤：**

1. **创建 Netlify 账号**
   - 访问 [Netlify](https://www.netlify.com) 注册免费账号

2. **连接 GitHub 仓库**
   - 登录后点击 "Add new site" → "Import an existing project"
   - 选择 "GitHub" 并授权
   - 选择你的 `questionnaire-app` 仓库

3. **配置部署**
   - Build command: 留空
   - Publish directory: 留空（默认根目录）
   - 点击 "Deploy site"

4. **获取访问链接**
   - 部署完成后，Netlify 会提供一个随机域名
   - 可以在 "Site settings" 中自定义域名

### 方案3：Vercel

**优势：**
- 完全免费
- 对前端项目特别友好
- 自动部署和预览
- 支持自定义域名
- 自动 HTTPS

**部署步骤：**

1. **创建 Vercel 账号**
   - 访问 [Vercel](https://vercel.com) 注册免费账号

2. **导入项目**
   - 登录后点击 "New Project"
   - 连接 GitHub 并选择你的仓库
   - 点击 "Import"

3. **部署配置**
   - Framework Preset: 选择 "Other"
   - Build Command: 留空
   - Output Directory: 留空
   - 点击 "Deploy"

### 方案4：Firebase Hosting

**优势：**
- Google 提供的服务，稳定可靠
- 免费额度足够个人使用
- 支持自定义域名
- 自动 HTTPS
- 全球 CDN

**部署步骤：**

1. **创建 Firebase 账号**
   - 使用 Google 账号登录 [Firebase Console](https://console.firebase.google.com)

2. **创建项目**
   - 点击 "Add project"
   - 输入项目名称（如 `questionnaire-app`）
   - 完成项目创建

3. **安装 Firebase CLI**
   ```bash
   npm install -g firebase-tools
   ```

4. **初始化项目**
   ```bash
   firebase login
   firebase init hosting
   ```
   - 选择你的 Firebase 项目
   - 公共目录：输入 `.`（当前目录）
   - 配置为单页应用：Yes

5. **部署项目**
   ```bash
   firebase deploy
   ```

## 部署后注意事项

### 数据存储限制
由于应用使用 localStorage 存储数据：
- **数据仅存储在用户浏览器中**，不同用户之间数据不共享
- **存储空间限制**：通常为 5-10MB
- **数据持久性**：用户清除浏览器数据会丢失问卷数据
- **隐私安全**：数据仅存储在本地，不会上传到服务器

### 功能限制
- 无法实现多用户协作编辑
- 无法进行实时数据同步
- 无法收集和汇总多用户的问卷回答

### 自定义域名配置
大多数免费托管服务都支持自定义域名：
1. 在域名注册商处设置 DNS 记录
2. 在托管服务的设置中添加自定义域名
3. 等待 DNS 传播（通常需要几分钟到几小时）

## 数据备份建议

由于使用 localStorage 存储数据，建议：
1. 定期使用 "导出CSV" 功能备份数据
2. 重要问卷数据及时下载保存
3. 考虑在未来升级为使用云数据库的版本

## 升级方案（未来扩展）

如果需要更强大的功能，可以考虑：
1. 添加后端服务（如 Firebase Realtime Database）
2. 使用云存储替代 localStorage
3. 实现用户认证和权限管理
4. 添加数据同步和备份功能

---

**部署完成后，你的问卷应用就可以通过互联网访问了！** 用户可以填写问卷，数据会自动保存在他们的浏览器中。