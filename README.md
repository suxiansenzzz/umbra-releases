<p align="center">
  <b>归影 Umbra</b><br>
  <sub>插上相机，剩下的交给我 · macOS 菜单栏 App</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/macOS-14%2B-1c1a17?style=flat-square&logo=apple&logoColor=ffffff" alt="macOS 14+">
  <img src="https://img.shields.io/badge/Swift-5-F05138?style=flat-square&logo=swift&logoColor=ffffff" alt="Swift 5">
</p>

---

## 这是什么仓库

**只放构建产物，不含源码。** 源码仓库是私有的，这里只提供可以直接下载运行的安装包，
以及配套的 Linux 服务端二进制。

安装包由私有仓库的 GitHub Actions 在每次发版时自动构建、自动上传，不是手工打包。

## 下载哪个

| 你的设备 | 下载文件 |
|---|---|
| Mac（Apple Silicon / Intel，通用二进制） | `Umbra-<版本>.zip` |
| Linux 服务端 · x86_64 | `umbra-server-linux-amd64.tar.gz` |
| Linux 服务端 · ARM64（群晖、威联通等） | `umbra-server-linux-arm64.tar.gz` |

到右侧 [Releases](../../releases) 页选最新版本下载。

## 安装 macOS 客户端

1. 解压 `Umbra-<版本>.zip`，把 `Umbra.app` 拖进「应用程序」。
2. **首次打开会被 Gatekeeper 拦下**：当前版本用 ad-hoc 签名、未做 Apple 公证。
   绕过方式：在 App 上 **右键 → 打开 → 再点「打开」**，之后双击就能正常启动。
3. 启动后不会弹窗口——它是纯菜单栏 App，只在菜单栏出现一枚环标，点它展开面板。
4. 系统要求 macOS 14 或更高；编译基线是 macOS 26，但在 14/15 上照常运行。

## 使用 Linux 服务端

```bash
tar -xzf umbra-server-linux-amd64.tar.gz
chmod +x umbra-server
UMBRA_DATA=/data/Umbra UMBRA_DB=/data/umbra.db UMBRA_ADDR=:8080 ./umbra-server
```

| 环境变量 | 作用 | 默认值 |
|---|---|---|
| `UMBRA_ADDR` | 监听地址 | `:8080` |
| `UMBRA_DATA` | 素材存放目录 | `/data/Umbra` |
| `UMBRA_DB` | SQLite 数据库路径 | `/data/umbra.db` |

二进制是纯静态的（`CGO_ENABLED=0`），目标机器不需要装 glibc 之外的任何依赖，也不需要额外编译工具。

## 关于

- 照片只在本机处理，不上传云端。
- 这个仓库不接受 PR（没有源码可改）；装了之后遇到问题，欢迎在 [Issues](../../issues) 里反馈，附上版本号与系统版本。
- 版本号对应私有仓库的 tag，更新日志见每个 Release 的说明。
