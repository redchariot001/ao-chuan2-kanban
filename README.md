# 奥传2 项目看板（GitHub Pages 静态托管）

这是《奥特曼传奇英雄2》项目看板 + 角色排期表的**永久在线托管版**，替代之前会休眠/会换域名的 CloudStudio 沙箱。

## 文件
- `index.html` — 项目进度看板
- `schedule.html` — 角色排期表
- `.github/workflows/pages.yml` — 自动部署到 GitHub Pages 的工作流

## 访问地址（部署后固定不变）
- 项目看板：`https://<你的用户名>.github.io/<仓库名>/`
- 角色排期表：`https://<你的用户名>.github.io/<仓库名>/schedule.html`

## 一次性初始化（只需做一次）

1. 注册/登录 GitHub（https://github.com，免费账号即可）
2. 右上角「+」→「New repository」
   - Repository name 填 `ao-chuan2-kanban`（或任意英文名）
   - 选择 **Public**（公开仓库才能免费启用 Pages）
   - 不要勾选 "Add a README"
   - 点 Create repository
3. 把本目录推上去（在终端执行，把 `你的用户名` 换成真实用户名）：

```bash
cd "C:/Users/nilei.JOY/WorkBuddy/2026-08-12-14-25-29/kanban-pages"
git init
git add .
git commit -m "init: 奥传2项目看板"
git branch -M main
git remote add origin https://github.com/你的用户名/ao-chuan2-kanban.git
git push -u origin main
```

4. 启用 Pages：仓库页 → Settings → Pages → Source 选 **GitHub Actions**（因为我们已经配好了 pages.yml，首次 push 会自动触发部署）
5. 等 1~2 分钟，Actions 页看到绿色 √ 即部署完成，访问上面的地址即可

## 以后每次更新内容（这才是关键）

以后石头调整开发计划、改角色/日期/制作人，我只需更新 `index.html` / `schedule.html`，然后：

```bash
cd "C:/Users/nilei.JOY/WorkBuddy/2026-08-12-14-25-29/kanban-pages"
git add .
git commit -m "update: <本次变更摘要>"
git push
```

GitHub Actions 会自动重新部署，**URL 永久不变、永不休眠、永不过期**。

## 注意事项
- 仓库必须 **Public**，Private 仓库免费版不支持 Pages
- 如果不想公开，可用 Cloudflare Pages / Netlify（也免费、支持私有仓库，URL 同样永久固定）
- 之后我会把这个「推送到 GitHub Pages」的流程固化到 `dev-plan-sync` 技能里，以后同步看板时自动改用它，不再用会休眠的沙箱
