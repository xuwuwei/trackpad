# RemotePadServer

PC端键盘/触摸板模拟器 - 将手机/平板变成无线键盘和触摸板

## 下载

访问 [Releases](https://github.com/xuwuwei/trackpad/releases) 页面下载最新版本。

### macOS 版本

我们提供两个版本的 macOS 安装包：

- `RemotePadServer_x.x.x_x64.dmg` - Intel Mac (x86_64)
- `RemotePadServer_x.x.x_aarch64.dmg` - Apple Silicon Mac (M1/M2/M3)

**⚠️ 重要提示：解决"已损坏"问题**

由于应用没有 Apple Developer 签名，首次运行时 macOS 会提示"已损坏"。这不是真的损坏，只是 macOS 的安全限制。请按以下步骤解决：

#### 方法1：终端命令（推荐）

```bash
# 1. 打开终端

# 2. 运行以下命令（将路径替换为实际的应用路径）
sudo xattr -rd com.apple.quarantine /Applications/RemotePadServer.app

# 3. 输入管理员密码（输入时不会显示）

# 4. 再次打开应用即可
```

#### 方法2：系统偏好设置

1. 打开 **系统偏好设置** → **安全性与隐私** → **通用**
2. 点击左下角的锁图标解锁
3. 在底部会看到"已阻止使用 RemotePadServer"，点击 **仍要打开**

#### 方法3：直接运行（临时）

```bash
# 直接从终端运行，绕过 Gatekeeper
/Applications/RemotePadServer.app/Contents/MacOS/RemotePadServer
```

### Windows 版本

- `RemotePadServer_x.x.x_x64-setup.exe` - 安装程序
- `RemotePadServer_x.x.x_x64.msi` - MSI 安装包

Windows 版本直接下载运行即可，没有额外的安全限制。

## 功能特性

- **键盘模拟**: 接收网络事件并模拟键盘按键
- **触摸板模拟**: 接收触摸事件并模拟鼠标移动
- **网络通信**: 支持UDP和TCP协议
- **mDNS服务**: 自动发现局域网内的服务
- **系统托盘**: 在任务栏/菜单栏显示图标和菜单
- **二维码显示**: 生成连接二维码供手机扫描
- **开机启动**: 设置程序开机自启动

## 使用方法

1. **启动程序**
   - macOS: 双击打开应用
   - Windows: 运行安装程序后从开始菜单启动

2. **查看连接信息**
   - 程序启动后会显示IP地址和端口
   - 默认端口：UDP 8080, TCP 8081

3. **扫描二维码连接**
   - 用 RemotePad App 扫描显示的二维码即可连接

4. **设置开机启动**
   - 在托盘菜单中选择开机启动选项

## 项目结构

```
link/
├── src-tauri/          # Tauri 后端代码
│   ├── src/            # Rust 源代码
│   └── Cargo.toml      # Rust 配置
└── ui/                 # 前端界面
    ├── app.js
    ├── index.html
    └── style.css
```

## 开发构建

### 前置要求

- [Rust](https://rustup.rs/)
- [Node.js](https://nodejs.org/)

### 构建步骤

```bash
cd link

# 安装依赖
npm install

# 开发模式运行
cargo tauri dev

# 构建发布版本
cargo tauri build
```

## 许可证

MIT License
