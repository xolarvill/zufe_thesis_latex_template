# 浙江财经大学学位论文 LaTeX 模板（`zufe-thesis`）

本模板严格遵循《浙江财经大学博士、硕士学位论文撰写规定》（2025年版），支持**硕士/博士**、**盲审/答辩/正式**三种版本，适用于 XeLaTeX 编译，开箱即用。

---

## 功能特性

- 完整支持学校规定的 **10 大构成要件**（封面、声明、中英文扉页、摘要、目录、正文、参考文献、附录、致谢、封底）
- 自动区分 **盲审版**（自动隐藏作者/导师/致谢/发表论文等敏感信息）
- 中英文摘要格式严格对标：  
  - “ABSTRACT” 三号加粗、2 倍行距、段前 2 行、段后 1 行  
  - 关键词自动转小写、分号分隔
- 公式编号 `(2.2)`、图表编号 `图2-1` / `表2-1` 符合规范
- 页眉、页脚、页码、边距、字体、行距等排版细节完全合规
- 支持本地 TTF 字体文件（确保跨平台一致性）
- 参考文献采用 `biblatex + gb7714-2015`，作者-年份引用格式
- zufe-thesis.cls 已内置 18+ 个排版必需宏包，覆盖页面、字体、图表、参考文献、页眉页脚等全部格式要求。用户只需在 main.tex 中添加学科专用宏包（如 amsmath、algorithm 等）。

```bash
## 📦 文件结构
zufe-thesis/
├── zufe-thesis.cls # 核心文档类
├── example.tex # 完整示例文档（脱敏版）
├── example.bib # 示例参考文献库
├── README.md # 本说明文件
└── fonts/ # （可选）存放本地字体文件
├── SimSun.ttf
├── SimHei.ttf
└── KaiTi.ttf
```

## 🛠️ 使用方法

### 1. 编译环境要求

- **编译引擎**：`XeLaTeX`（必须）
- **依赖宏包**：`ctex`, `fontspec`, `xeCJK`, `biblatex`, `biber`, `geometry`, `fancyhdr` 等（TeX Live 2020+ 或 MiKTeX 最新版通常已包含）

### 2. 基本使用步骤

a）命令行

```bash
# 编辑主文档（如 main.tex）
xelatex main.tex
biber main       # 生成参考文献
xelatex main.tex
xelatex main.tex # 最终生成完整 PDF
```

b）SublimeText

首先选择`Tools` $\rightarrow$ `Build with` $\rightarrow$ `LaTeX - Traditional Builder with Xelatex`。
编写完成之后用`CMD`+`B`编译。


c）其他类似带有支持LaTeX的编译器

确认使用xelatex编译后使用。


### 3. 文档类选项
在 \documentclass 中指定：

```latex
% 学位类型 + 版本
\documentclass[master, blind]{zufe-thesis}   % 硕士盲审版
\documentclass[doctor, defense]{zufe-thesis} % 博士答辩版
\documentclass[master, final]{zufe-thesis}   % 硕士正式版（默认）
```

### 4. 设置基本信息
```latex
\submitDate{2025年6月}      % 中文扉页
\submitDateEN{June 2025}    % 英文扉页（避免显示中文）
```

### 5. 自定义字体（可选）
取消注释并指定本地字体路径：

```latex
\setCJKmainfont[Path=./fonts/]{SimSun.ttf}
\setCJKsansfont[Path=./fonts/]{SimHei.ttf}
\setCJKmonofont[Path=./fonts/]{KaiTi.ttf}
\setmainfont[Path=./fonts/]{TimesNewRoman.ttf}
```

## 📝 注意事项
- 不要手动修改 .cls 文件，除非你明确知道自己在做什么。
- 盲审版会自动省略：声明页、致谢、发表论文列表。
- 图表较多时，可手动添加图目录/表目录（学校未强制要求）。

若遇编译错误，请确保：
- 使用 XeLaTeX + Biber
- 系统已安装中文字体（或提供本地 TTF）
- .bib 文件编码为 UTF-8

## 参考依据
- 《浙江财经大学博士、硕士学位论文撰写规定》（2025）
- GB/T 7714-2005《文后参考文献著录规则》
- ctex 宏包文档
