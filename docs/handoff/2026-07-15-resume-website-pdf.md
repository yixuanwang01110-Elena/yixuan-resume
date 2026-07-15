# Handoff — 王奕萱个人简历网页 + 双语 PDF 导出

- **日期**: 2026-07-15
- **类型**: reference(建置已完成并上线,本文件供后续修改时快速接手)
- **Branch**: main(仓库 `yixuanwang01110-Elena/yixuan-resume`)

## 状态摘要

1. 双语(中/英切换)个人简历网页已上线 GitHub Pages:https://yixuanwang01110-elena.github.io/yixuan-resume/
2. 单文件架构:`index.html` 含全部 CSS/JS,照片以 base64 内嵌;`?lang=en` 参数可直开英文版
3. 移动端已专项打磨:viewport、吸顶目录栏、语言按钮固定首屏右上、2 列卡片;微信打开正常(旧缓存问题用 `?v=N` 参数绕过)
4. 桌面端左侧有滚动联动的交互目录;设计体系为象牙沙底 + 青瓷/雾青/沙金/雾蓝/陶土莫兰迪色、圆角面板、楷体名字、深色渐变页脚
5. 打印样式(`@media print`)完成:`@page margin:0` 底色满铺无白边、双栏紧凑、面板整体分页;中英文 PDF 各 **2 页**
6. PDF 产物在 `/Users/wangyixuan/Downloads/简历/`:`王奕萱-简历-中文.pdf`、`Yixuan-Wang-Resume-EN.pdf`

## 必读文件

- `index.html` — 唯一源文件;语言用 `.zh`/`.en` span + `data-lang` 切换;打印样式在 `<style>` 末尾的 `@media print` 块
- `/Users/wangyixuan/.claude/projects/-Users-wangyixuan-Downloads---/memory/yixuan-resume-website.md` — 项目记忆:内容红线(保守数据、不放手机号、不公开 PulpaTronics 客户 pipeline)、用户审美偏好(忌暖黄 AI 味/印章/花哨名字特效)
- `/Users/wangyixuan/Downloads/简历/Elena_Wang_Resume_Master_Inventory_CN.docx` — 完整个人经历素材库(新增内容从这里取)

## 常用操作

- **改网页**: 编辑 `index.html` → `git commit && git push` → 1–2 分钟生效,网址不变
- **重新导出 PDF**(Chrome 未装,用 Edge):
  ```bash
  EDGE="/Applications/Microsoft Edge.app/Contents/MacOS/Microsoft Edge"
  cd /Users/wangyixuan/Downloads/简历
  "$EDGE" --headless --disable-gpu --no-pdf-header-footer --virtual-time-budget=4000 \
    --print-to-pdf="王奕萱-简历-中文.pdf" "file://$PWD/website/index.html?lang=zh"
  # 英文版换 ?lang=en 与对应文件名 Yixuan-Wang-Resume-EN.pdf
  ```
- **PDF 分页原则**: 所有 `.panel/.row/.case/.strength/.skill` 均 `break-inside: avoid`;若内容增加导致超 2 页,优先调 `@media print` 内的字号/内边距,并有 `[data-lang="en"]` 专用的更紧规则

## 已知问题 / 注意

- GitHub Pages 国内无法稳定访问 → 国内投递以 PDF 附件为主(用户已决定不做镜像站)
- 微信内置浏览器缓存旧版页面:测试时给链接加 `?v=N` 新参数即可绕过
- 楷体名字依赖 macOS/iOS 的 Kaiti SC;Windows 回退 KaiTi/宋体,视觉略有差异

## 下一步(如有新 session)

- 无未完事项。可能的后续:内容更新(新经历/数据核实后替换保守表述)、按投递方向微调文案、重新导出 PDF
