# 🧾 Windows Terminal Preview Context Menu

![wt.1](https://raw.githubusercontent.com/rescenic/wt.context.menu/master/3-test.png)

# Feature

-   Two layers of context menu
-   Auto parse settings.json to contruct menu
-   With uninstaller

# Todo

-   [x] Custom icon for profile

# Install

1. Clone this repo
   `git clone https://github.com/rescenic/wt.context.menu`
2. Configure your settings.json in Windows Terminal Preview folder & config.json
   `C:\Users\%USERNAME%\AppData\Local\Packages\Microsoft.WindowsTerminalPreview_8wekyb3d8bbwe\LocalState\settings.json`
   ![wt.2](https://raw.githubusercontent.com/rescenic/wt.context.menu/master/1-configure.png)
3. Copy folder `icons` to `C:\Users\%USERNAME%\AppData\Local\Packages\Microsoft.WindowsTerminalPreview_8wekyb3d8bbwe\LocalState\icons\`
4. Run powershell (no need to get admin access right)
5. Change the execution policy `Set-ExecutionPolicy Unrestricted -scope CurrentUser`
6. Run `SetupContextMenu.ps1` script
   ![wt.3](https://raw.githubusercontent.com/rescenic/wt.context.menu/master/2-install.png)
   ![wt.4](https://raw.githubusercontent.com/rescenic/wt.context.menu/master/4-compare.png)
   ![wt.5](https://raw.githubusercontent.com/rescenic/wt.context.menu/master/5-wtpreview.png)

# Uninstall

1. Run `SetupContextMenu.ps1 -uninstall:$true`

# Config

This script will parse the `settings.json` file to generate menu items. However you can customize it.  
Put any icon file into `icon` folder and modify the `config.json` like the following.

```json
{
    "global": {
        "extended": false
    },
    "profiles": {
        "{a5a97cb8-8961-5535-816d-772efe0c6a3f}": {
            "icon": "arch.ico",
            "label": "Arch Linux"
        },
        "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}": {
            "showRunAs": true
        },
        "{b453ae62-4e3d-5e58-b989-0a998ec441b8}": {
            "hidden": true
        }
    }
}
```

**Config reference**

-   global
    -   extended[bool]: if set this to true, context menu will only show up when right click with `shift`
-   profiles
    -   guid[string]: this GUID of your profile defined in `settings.json`
        -   hidden[bool]: overwrites the visibility of the profile, if defined
        -   icon[string]: filename of your ico file, **you must put this file in icon folder**
        -   label[string]: context menu label
        -   showRunAs[bool]: add `run as administrator` item for this profile

# Misc

I'm not sure that icons file are legal or not. If you feel it is not ok, please tell me. Thanks.
