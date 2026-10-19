# 上传到 GitHub

本文件夹就是仓库根目录。无需上传外层 ZIP、`node_modules` 或个人阅读备份。

## 方法一：GitHub Desktop（图形界面）

1. 解压 `ReadSpace-GitHub.zip`，找到包含 `package.json` 的 `readspace` 文件夹。
2. 打开 GitHub Desktop，使用 **File → Add local repository** 选择该文件夹。
3. 因为源码包不含 `.git`，选择界面中创建仓库的链接，在现有文件夹中初始化仓库；首次提交这些源码。
4. 点击 **Publish repository**，设置仓库名，例如 `readspace`，并选择是否保留为私有仓库。
5. 发布后，在 GitHub 检查根目录是否出现 `package.json`、`README.md`、`app/`、`.openai/hosting.json` 和 `.github/workflows/check.yml`。

## 方法二：命令行

先在 GitHub 新建一个空仓库，不要提前勾选 README、LICENSE 或 .gitignore。在解压后的 `readspace` 文件夹中执行：

```bash
git init
git add .
git commit -m "Initial ReadSpace source"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/readspace.git
git push -u origin main
```

将 `YOUR_USERNAME` 和仓库名替换为你的实际值；认证按 GitHub / Git 的提示完成。首次使用 Git 时，可能需要先设置提交作者姓名与邮箱。

## 方法三：网页上传

在空仓库选择 **uploading an existing file / Add file → Upload files**，上传解压后的文件和目录，填写提交说明后保存。不要只上传 ZIP，否则 GitHub 里无法直接浏览和运行项目。

网页上传时尤其注意隐藏目录 `.openai` 和 `.github`。Windows 资源管理器可启用“查看 → 显示 → 隐藏的项目”；如果浏览器未保留这些目录，请使用上面的 GitHub Desktop 或命令行方法。

根目录必须直接包含 `package.json`，不要再多套一层 `readspace/readspace`。

## 上传后的检查

- 在其他目录克隆仓库，按 README 执行 `npm ci` 和 `npm run dev`。
- GitHub 的 Actions 页可以查看依赖安装、测试、类型检查和构建结果。
- 源码包没有原站点部署身份，上传不会改动正在使用的 ReadSpace 网站。
- 学习记录请在旧网站“设置与备份”中导出，再在新站点手动导入；它们不会保存在仓库里。
