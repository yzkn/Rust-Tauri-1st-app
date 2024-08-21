# Tauri-1st-app

---

# 環境準備

## Windows環境

- [Microsoft C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/)
  - C++によるデスクトップ開発

- [WebView2](https://developer.microsoft.com/en-us/microsoft-edge/webview2/#download-section)はWindows11に標準で含まれているのでスキップ
  - Evergreen Bootstrapper

- [Rust](https://www.rust-lang.org/tools/install)
  - [rustup-init.exe (64-bit)](https://static.rust-lang.org/rustup/dist/x86_64-pc-windows-msvc/rustup-init.exe)

- [WinGet](https://www.microsoft.com/p/app-installer/9nblggh4nns1)
  - Voltaを `winget` コマンドでインストールする場合

- Volta
  - Windows Terminalを開いて以下のコマンドを実行

```powershell
winget install Volta.Volta
volta install node # Nodeの最新LTS版
volta install npm
```

### Windows環境でAndroidアプリを作る場合

- [Android Studio](https://developer.android.com/studio)
  - SDK Managerで以下をインストール

```plaintext
Android SDK Build-Tools
Android SDK Command-line Tools
Android SDK Platform （最新バージョンの数字のもの）
Android SDK Platform-Tools
NDK (Side by side)
```

- 環境変数を設定

```powershell
[System.Environment]::SetEnvironmentVariable("JAVA_HOME", "C:\Program Files\Android\Android Studio\jbr", "User")
[System.Environment]::SetEnvironmentVariable("ANDROID_HOME", "$env:LocalAppData\Android\Sdk", "User")
$VERSION = Get-ChildItem -Name "$env:LocalAppData\Android\Sdk\ndk"
[System.Environment]::SetEnvironmentVariable("NDK_HOME", "$env:LocalAppData\Android\Sdk\ndk\$VERSION", "User")
```

- rustupでターゲットを追加

```powershell
rustup target add aarch64-linux-android armv7-linux-androideabi i686-linux-android x86_64-linux-android
```

## Mac

- Xcode

- Volta
  - Terminalを開いて以下のコマンドを実行

```zsh
brew install volta
volta install node # Nodeの最新LTS版
volta install npm
```

- [Rust](https://www.rust-lang.org/tools/install)

```zsh
curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
```

# プロジェクト作成

```powershell
$env:CTA_ARGS="--rc"; irm https://create.tauri.app/ps | iex
```

```plaintext
? Project name (tauri-app) ? <Enter key>

? Identifier (com.tauri-app.app) ? <Enter key>

? Choose which language to use for your frontend ?
? TypeScript / JavaScript  (pnpm, yarn, npm, bun)
  Rust 
  .NET 
<Enter key>

? Choose your package manager ?
  pnpm
  yarn
? npm
  bun
<↓><↓><Enter key>

? Choose your UI template ?
? Vanilla
  Vue
  Svelte
  React 
  Solid
  Angular
  Preact
<Enter key>

? Choose your UI flavor ?
? TypeScript
  JavaScript
<Enter key>
```

```powershell
cd tauri-app
npm install
npm run tauri dev
```

コンパイルが完了すると、自動的にアプリケーションのウィンドウが開き、[コンテンツ](http://localhost:1420/)が表示される。

---
