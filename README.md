# PDF 密码保护页面

这是一个简单的静态密码保护页面，部署在 GitHub Pages 上。

## ⚠️ 安全提示

这种方案只能防普通用户。PDF 文件仍然在仓库中，懂技术的人可能通过仓库或直接文件链接访问到文件。

## 文件说明

- `index.html`：密码输入页面
- `document.pdf`：要保护的 PDF 文件

## 修改密码

打开 `index.html`，找到这一行：

```javascript
const CORRECT_PASSWORD = "123456";
```

把 `123456` 改成你想要的密码。

## 部署到 GitHub Pages

### 第一步：创建 GitHub 仓库

1. 打开 [github.com](https://github.com)，登录账号
2. 点击右上角 `+` → `New repository`
3. 仓库名随便取，例如 `pdf-password-site`
4. 选择 `Public`（公开仓库）
5. 点击 `Create repository`

### 第二步：上传文件

#### 方法一：网页直接上传（最简单）

1. 在仓库页面点击 `Add file` → `Upload files`
2. 把 `index.html` 和 `document.pdf` 拖进去
3. 点击 `Commit changes`

#### 方法二：用 Git 命令上传

如果你电脑上有 Git：

```bash
cd pdf-password-site
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/你的用户名/仓库名.git
git push -u origin main
```

### 第三步：开启 GitHub Pages

1. 在仓库页面点击 `Settings`
2. 左侧菜单找到 `Pages`
3. 在 `Branch` 下拉框选择 `main`，然后点击 `Save`
4. 等待 1-2 分钟，页面上会出现访问链接：
   ```
   https://你的用户名.github.io/仓库名/
   ```

## 绑定自己的域名

如果你有自己的域名，可以这样绑定：

1. 在 `pdf-password-site` 文件夹里创建一个 `CNAME` 文件，里面写上你的域名，例如：
   ```
   www.yourdomain.com
   ```
2. 把 `CNAME` 文件一起上传到 GitHub
3. 去你的域名服务商那里，添加 DNS 记录：
   - 类型：`CNAME`
   - 主机记录：`www`
   - 记录值：`你的用户名.github.io`
4. 等待 DNS 生效（通常几分钟到几小时）
5. 在 GitHub 仓库的 `Settings → Pages → Custom domain` 里输入你的域名，点击 `Save`

## 访问测试

打开生成的链接，输入密码 `123456`，应该就能看到 PDF 内容。
