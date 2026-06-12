---
title: "Minimize, maximize, close buttons on the Gnome's top bar"
date: 2024-04-13
forum: Desktop Environments
---

### Post by Shishimaru on 2024-04-13
[COLOR=#0C0D0E][FONT=-apple-system][SIZE=3][FONT=var(--theme-post-body-font-family][FONT=inherit]I am using Ubuntu 24.04 with the latest Gnome, and I am trying to make some use for the top panel which stays there just for some icons and nothing else.[/FONT]
[FONT=inherit]Remembering the Unity desktop, which still exists with some kind of limitations like (maybe?) missing Wayland or missing some features or options, I was wondering if it's possible to maximize an app and have on the top bar: the windows commands like min/maximize/close and, eventually, the global menu. I've found some very old articles on the web which are confusing or not updated, so I thought to ask here in case anybody has any suggestions.[/FONT]
[FONT=inherit]Thanks in advance.[/FONT]
[/FONT][/SIZE]
[/FONT][/COLOR]

---

### Post by vanadium on 2024-04-14
The Gnome Shell extension "Unite" can display the window title and window controls in the topbar. It also can enable tray icons. It will remove the legacy title bar of maximized applications.

---

### Post by Frogs Hair on 2024-04-15
Ubuntu Unity is now an official flavor if interested. 24.04 will be released on April 25th.
[https://ubuntuunity.org/](https://ubuntuunity.org/)

---

### Post by james12215 on 2024-04-18
To maximize an application window and have the window controls (minimize, maximize, close) and potentially the global menu on the top panel in Ubuntu 24.04 with GNOME, you can try the following steps:
For more details.


1. **Install GNOME Shell Extensions**:
   - Ensure you have GNOME Shell Extensions installed on your system. You can install it from the Ubuntu Software Center or via the command line with:
     ```
     sudo apt install gnome-shell-extensions
     ```


2. **Install "Pixel Saver" Extension**:
   - "Pixel Saver" is a GNOME Shell extension that maximizes screen real estate by merging the title bar and the top panel, similar to the behavior in Unity. You can install it from the GNOME Extensions website (extensions.gnome.org) or through the GNOME Tweaks tool.


3. **Enable "Pixel Saver" Extension**:
   - Once installed, open the GNOME Tweaks tool (you can install it from the Ubuntu Software Center if you don't have it already).
   - Navigate to the "Extensions" tab.
   - Find "Pixel Saver" in the list of installed extensions and toggle it to enable.


4. **Configure "Pixel Saver" Extension**:
   - After enabling the extension, you may want to configure its settings.
   - Open GNOME Tweaks and navigate to the "Extensions" tab.
   - Click on the gear icon next to "Pixel Saver" to access its settings.
   - Here, you can customize the behavior of the extension,

---

### Post by vanadium on 2024-04-18
@james12215, Pixel Saver is not yet updated for Gnome 45, leave alone Gnome 46 that will be the Gnome edition on the next LTS.

For Unite, I need to make a correction. You *still* do not find it on Gnome Shell Extensions, but you can install an up-to-date version from the [github page](https://github.com/hardpixel/unite-shell). I see it on the Gnome Shell Extensions because I have it installed, but it will not show up when the filter is set to "Current version" and your Gnome Shell version is higher than 44. The developer does not want to put it on Gnome Shell Extensions anymore. Unfortunately, I do not find the message back where he stated the reasons.

---

