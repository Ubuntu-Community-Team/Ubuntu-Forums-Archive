---
title: "Unity-2D with XFWM4"
date: 2011-11-08
forum: Desktop Environments
---

### Post by quequotion on 2011-11-08
How to get Unity-2D to work with xfwm4:

```
sudo apt-get install xfwm4
```You don't need to install the entire xfce/xubuntu desktop.```
gksu gedit /usr/share/gnome-session/sessions/ubuntu-2d.session /usr/share/applications/xfwm4.desktop
```In **ubuntu-2d.session** replace:```
DefaultProvider-windowmanager=metacity
``` with:```
DefaultProvider-windowmanager=xfwm4
```In **xfwm4.desktop** (which should be a new, empty file):```
[Desktop Entry]
Type=Application
Name=Xfwm4
Exec=xfwm4
NoDisplay=true
# name of loadable control center module
X-GNOME-WMSettingsModule=xfwm4
# name we put on the WM spec check window
X-GNOME-WMName=Xfwm4
# back compat only 
X-GnomeWMSettingsLibrary=xfwm4
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=xfwm4
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-Phase=WindowManager
X-GNOME-Provides=windowmanager
X-GNOME-Autostart-Notify=true
X-Ubuntu-Gettext-Domain=xfwm4
```There may be some better options for the .desktop file. Particularly I couldn't find any hints about what X-GNOME-WMSettingsModule should be.

You can modify the xfwm4 configuration with: **xfwm4-settings**, **xfwm4-tweaks-settings**, and **xfwm4-workspace-settings**. For some reason, these applications will not show up in the menu (they should be in the menu as "xfce settings" etc).

Attached screenshot shows unity-2d panel, nautilus, and gome-terminal in xfwm with composting (activate in xfwm-tweaks-settings)

---

### Post by quequotion on 2011-11-08
Of course, xfwm4 is not designed for unity.

There are a few rough edges, like window decorations don't blend into the panel on maximize and the panel sometimes has a border like an ordinary window. The Smallscreen theme makes these relatively painless.

Here's the screenshot I mentioned before.

---

