# GitHub Actions 构建说明

## 构建配置

这个GitHub Actions工作流会自动构建GH Injector Library项目，生成以下文件：

### 构建输出

**x86平台 (32位):**
- `GH Injector - x86.dll` - 主要注入器库
- `GH Injector DNP - x86.dll` - .NET注入库  
- `GH Injector SM - x86.exe` - Shell Manager可执行文件

**x64平台 (64位):**
- `GH Injector - x64.dll` - 主要注入器库
- `GH Injector DNP - x64.dll` - .NET注入库
- `GH Injector SM - x64.exe` - Shell Manager可执行文件

### 构建流程

1. **构建阶段**: 分别为x86和x64平台构建Release版本
2. **打包阶段**: 将所有构建产物整合到一个完整的发布包中

### 下载构建产物

构建完成后，可以在GitHub Actions的Artifacts部分下载：

- `GH-Injector-Release-x86` - x86平台的构建产物
- `GH-Injector-Release-x64` - x64平台的构建产物  
- `GH-Injector-Complete-Package` - 包含所有平台的完整发布包

### 触发条件

- 推送到main或master分支
- 创建Pull Request到main或master分支
- 手动触发 (workflow_dispatch)

### 技术细节

- 使用Visual Studio 2022构建工具
- 支持C++20标准
- 使用Windows 10 SDK
- 最小化构建过程，无代码检查步骤