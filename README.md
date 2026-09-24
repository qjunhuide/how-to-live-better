# 高性价比人生指南 · 在线阅读页

一个单文件 HTML 阅读页，把开源书《高性价比人生指南》的全部 32 节、528 条建议
渲染成可搜索的页面。手机上打开就能看，不用装任何东西。

**在线阅读：** https://cdyforever.github.io/how-to-live-better/

## 这是什么

原书由 [eternity4719/HowToLiveBetter](https://github.com/eternity4719/HowToLiveBetter)
维护（Unlicense，公有领域），按「性价比」排序，每条写清花掉什么、换回什么、证据多硬，
只引期刊论文和官方文件。

本仓库不是原书的 fork，也不改动原书内容。它只做一件事：把原书正文渲染成一个
**自包含的单文件网页**，方便在手机和别人的电脑上直接打开。

## 页面特性

- **零外部资源**：没有 CDN、没有字体外链、不 fetch 任何数据，断网也能读
- 逐条卡片：建议标题、证据等级（A/B/C）、性价比档、成本标签
- **「说人话」高亮块**——原书里这一栏专门把统计量翻成日常说法，页面上做得最显眼
- 全站关键词搜索（结果高亮）、只看 A 级、只看说人话
- 左侧目录带性价比色点，滚动联动
- 手机端：搜索框独占一行、顶栏向下滚动后自动收成一行、回到顶部按钮
- 明暗主题切换
- 支持直接打印

## 个人化阅读层

这个版本在不改动上游正文的前提下，额外提供：

- 「重点」筛选：快速聚焦身体底盘、精力、时间、金钱、应急、账号安全、长期学习、就医和体态等章节
- 快捷入口：身体底盘、精力管理、时间与执行、长期学习、体态与身体
- 收藏与继续阅读：点击每条右侧星标收藏，页面会记住上次读到的位置

收藏和阅读位置只保存在当前浏览器，不会上传，也不会随着上游内容更新丢失。

## 本地使用

不用构建，双击 `index.html` 即可。

## 重新生成

```bash
# 需要先有一份上游仓库的本地克隆
git clone --depth 1 https://github.com/eternity4719/HowToLiveBetter.git /tmp/upstream

# 全部 32 节
python build.py all -o index.html --repo /tmp/upstream

# 只做某几节
python build.py 1 2 16 --repo /tmp/upstream
```

源目录也可以用环境变量 `HLTB_REPO` 指定。

统计口径（条目数、A/B/C 分级、性价比三档）与上游的 `tools/sync-stats.ps1`
和 `index.html` 保持一致，生成结果可与上游徽章逐项对照。

## 自动更新

`.github/workflows/rebuild.yml` 每天 06:00（北京时间）拉取上游重新生成，
内容有变化才提交。也可以去 Actions 页面手动触发。

GitHub Pages 由 Actions 发布：普通推送会触发 `deploy-pages.yml`；每日重建任务也会在
重建后直接发布，因此不会依赖 GitHub Pages 的旧式分支发布方式。

## 授权

原书内容为 Unlicense（公有领域）。本仓库的构建脚本同样不作任何权利保留。
