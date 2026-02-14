# Niri 配置目录

## 目录概述

这是 Niri Wayland 窗口合成器的配置目录。Niri 是一个实验性的 Wayland 合成器，专注于提供类似于 i3 的平铺窗口管理体验，同时支持 Wayland 的现代特性。

## 主要文件

### `config.kdl`
这是 Niri 的主配置文件，使用 KDL (KDL Document Language) 格式。该配置文件包含以下主要部分：

- **输入设备配置** (`input`): 键盘、触摸板、鼠标等输入设备的设置
  - 键盘布局: 当前使用 Colemak 变体
  - 触摸板: 启用了点击和自然滚动
  - NumLock: 启动时自动开启

- **输出配置** (`output`): 显示器设置（当前被注释掉）
  - 支持分辨率、刷新率、缩放、旋转和位置设置

- **布局配置** (`layout`): 窗口布局和外观设置
  - 间隙: 16 逻辑像素
  - 焦点环: 活跃状态为蓝色 (#7fc8ff)，非活跃状态为灰色 (#505050)
  - 边框: 当前禁用
  - 阴影: 当前禁用，但配置了柔和度为 30、扩展为 5、偏移为 (0, 5) 的参数

- **启动进程** (`spawn-at-startup`): 启动时自动运行的程序
  - waybar: 状态栏

- **窗口规则** (`window-rule`): 针对特定窗口的行为规则
  - WezTerm: 设置为空默认列宽以解决初始配置 bug
  - Firefox 画中画: 默认以浮动窗口打开

- **快捷键绑定** (`binds`): 全面的键盘快捷键配置
  - 应用启动: Mod+T (alacritty), Mod+D (fuzzel), Super+Alt+L (swaylock)
  - 媒体控制: 音量、播放控制、亮度调节
  - 窗口管理: 焦点移动、窗口移动、工作区切换
  - 布局控制: 列宽调整、窗口高度调整、最大化、全屏
  - 浮动窗口: Mod+V 切换浮动/平铺
  - 截图: Print (窗口), Ctrl+Print (屏幕), Alt+Print (窗口)
  - 系统控制: Mod+Shift+E 退出, Mod+Shift+P 关闭显示器

## 使用方式

### 配置文件位置
- 主配置: `~/.config/niri/config.kdl`
- 当前工作目录: `/home/red/.config/niri`

### 修改配置
1. 直接编辑 `config.kdl` 文件
2. Niri 支持热重载配置（通常通过 `niri msg action reload-config` 或类似命令）

### 查看配置选项
完整配置文档请访问: https://yalter.github.io/niri/Configuration:-Introduction

### 常用命令
- 查看输出信息: `niri msg outputs`
- 获取键名: 使用 `wev` 等工具查看 XKB 键名

## 注意事项

- 配置文件使用 KDL 格式，注释以 `//` 开头
- 使用 `/-` 可以注释掉整个节点
- "Mod" 修饰符在 TTY 上等于 Super，在 winit 窗口中等于 Alt
- 修改 `prefer-no-csd` 选项后需要重启应用程序才能生效
- 截图默认保存到 `~/Pictures/Screenshots/` 目录，文件名包含时间戳