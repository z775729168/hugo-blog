---
title: "Taskbar Stats 任务栏上显示系统信息"
date: 2021-05-07T16:18:36+08:00
draft: true
---

![taskbar-stats](https://cdn.jsdelivr.net/gh/z775729168/imgbed@master/img/taskbar-stats.webp)

**注意：首次安装时，您可能必须右键单击任务栏2次以显示TaskbarStats菜单。**

本体就是几个dll，通过安装包可以找到文件。绿化也非常简单，作者在github上也有脚本。举个例子。

```cmd
#install.cmd
@echo off

NET SESSION >nul 2>&1
IF %ERRORLEVEL% NEQ 0 (
    ECHO Please run as Administrator
    pause
    exit
)

cd /d %~dp0

regsvr32 /s CpuRam.dll
regsvr32 /s CpuRamPercent.dll
regsvr32 /s DiskSpeed.dll
regsvr32 /s NetSpeed.dll
regsvr32 /s NetSpeedBit.dll
```

```cmd
#uninstall.cmd
@echo off

NET SESSION >nul 2>&1
IF %ERRORLEVEL% NEQ 0 (
    ECHO Please run as Administrator
    pause
    exit
)

cd /d %~dp0

regsvr32 /u /s CpuRam.dll
regsvr32 /u /s CpuRamPercent.dll
regsvr32 /u /s DiskSpeed.dll
regsvr32 /u /s NetSpeed.dll
regsvr32 /u /s NetSpeedBit.dll

taskkill /F /IM explorer.exe > NUL & start explorer > NUL
```





