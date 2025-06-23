✅ 1. plan.md（项目开发计划）

# 项目名称：NetSplitX-Sing

## 项目简介

本项目基于 sing-box 网络引擎构建一个简洁高效的 IP/DNS 分流系统，集成 Tinc VPN 支持，并提供完整的 Web 可视化管理界面，支持规则上传、接口配置、状态查看、策略测试等。

---

## 模块结构

### 1. 后端（Go）
- 核心基于 sing-box，运行于 Ubuntu 24.04 容器中
- 新增协议模块：`protocol/tinc`（inbound/outbound）
- 配置读取 & API 控制：`internal/api/*`
- 配置文件按规则生成，JSON 格式，动态热更新

### 2. 前端（Vite + Naive UI）
- UI 技术栈：Vue 3 + Tailwind CSS + Naive UI
- 页面结构：

📂 分流控制中心
├── 接口设置
├── 规则管理
├── DNS 设置
├── 路由策略
├── Tinc VPN 管理
├── 日志查看
└── 分流测试

---

## 四类规则文件

- 国内 IP：`data/ipcn.txt`
- 国内域名：`data/domaincn.txt`
- 被墙 IP：`data/ip.txt`
- 被墙域名：`data/domain.txt`

规则支持导入、命中统计、Redis 缓存加速。

---

## 核心功能

- ✅ 支持双接口物理路由（物理口 + tun）
- ✅ 自动生成策略路由（ip rule / ip route / mark）
- ✅ DNS 分流（国内走系统 DNS，被墙走 DoH）
- ✅ 支持 DoH / DNSCrypt，禁止明文 53 解析
- ✅ 支持 Tinc VPN 创建、运行、hosts 管理
- ✅ 所有功能可通过 Web 控制，API 驱动热更新配置

---

## 运行入口

- sing-box 配置由 `backend/main.go` 启动并监听
- 前端编译为静态页面，嵌入 Go 后端或单独部署


⸻

