# NotePDF — Obsidian PDF 知识库助手

通用 PDF 转知识库助手插件。自动检测 Vault 中新增的 PDF 文件，生成索引笔记，支持 OCR 文字提取与智能关联。

## 功能特性

- **自动监控** — 检测 Vault 指定文件夹中的新 PDF 文件
- **模板引擎** — 支持自定义模板，自动生成索引笔记
- **OCR 文字提取** — 本地 Tesseract.js 或 AI API（OpenAI 兼容）双模式
- **智能关联** — 根据关键词推荐已有笔记并生成链接
- **PDF 归档** — 处理完成后自动将 PDF 移动到指定目录
- **批量处理** — 一键处理监控文件夹中的所有 PDF

## 安装

### 方法 1：手动安装

1. 下载本项目文件
2. 将 `manifest.json`、`main.js`、`styles.css` 复制到：
   `%APPDATA%\Obsidian\plugins\note-pdf\`
3. 在 Obsidian 中启用插件（设置 → 第三方插件 → NotePDF）

### 方法 2：符号链接（开发模式）

```bash
mklink /J "%APPDATA%\Obsidian\plugins\note-pdf" "E:\NotePDF-Plugin"
```

## 开发

```bash
# 安装依赖
npm install

# 开发模式（自动重编译）
npm run dev

# 生产构建
npm run build
```

## 使用方法

1. 在设置中配置监控文件夹（默认 `Inbox/`）
2. 将 PDF 文件放入监控文件夹
3. 插件自动生成索引笔记

也可以通过命令面板或右键菜单手动处理 PDF 文件。

## 设置说明

| 设置项 | 默认值 | 说明 |
|--------|--------|------|
| 监控文件夹 | Inbox/ | 监控的文件夹路径 |
| PDF 归档到 | Attachments/PDFs/ | 处理后 PDF 移动目标 |
| 索引笔记模板 | （内置默认） | 自定义模板文件路径 |
| 处理模式 | 自动 | 自动处理或手动确认 |
| OCR 模式 | 关闭 | 关闭/本地/AI API |
| 自动标签 | 双碳, 政策, ... | 逗号分隔的关键词 |
| 自动关联 | 开启 | 推荐已有相关笔记 |

## 模板占位符

| 占位符 | 说明 |
|--------|------|
| `{{title}}` | PDF 文件名 |
| `{{date}}` | 处理日期 |
| `{{time}}` | 处理时间 |
| `{{source}}` | 来源标识 |
| `{{tags}}` | YAML 标签 |
| `{{pages}}` | PDF 页数 |
| `{{pdf_relative_path}}` | PDF 相对路径 |
| `{{ocr_text}}` | OCR 文字（前 500 字） |
| `{{related_notes}}` | 关联笔记列表 |
| `{{tags_list}}` | 标签 Markdown 格式 |

## 隐私说明

- 本地 OCR 模式：数据不离开设备
- AI API 模式：数据仅传输到用户指定的 API 地址
- 插件不含任何遥测或统计代码

## 许可证

MIT License
