---
title: "Xgl/Compiz (Nvidia): hotkeys not functioning"
date: 2007-02-22
forum: Desktop Environments
---

### Post by bigbadsi on 2007-02-22
I've installed Compiz/Xgl for Nvidia using this guide: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29).  The Compiz hotkeys function inconsistently. 

Compiz itself works wonderfully except that the Compiz hotkeys (e.g. (Super-key + right-click) to zoom and (Ctrl + Alt + Left/Right Arrow) to switch workspaces) don't work until I change the Keyboard Layout Model under System > Preferences > Keyboard.  The hot keys then function as expected, until I restart X, when they do nothing again.  It doesn't seem to matter what I change the keyboard layout to, e.g. "Generic 104-key PC" or "Generic 105-key (Intl) PC", as long as the setting is changed.  My specific keyboard, the Saitek Eclipse, doesn't appear in the Keyboard model list.  The keyboard layout settings are kept between X restarts.

I sometimes get a small "gnome-panel" window appearing in the top left-hand corner of my desktop and I can't close this by right-clicking on the "gnome-panel" in the Window List.  Changing  the keyboard layout and restarting X/restarting the PC seems to stop this window appearing.

I've recently reinstalled on a new HD and then copied the contents of /home from the old disk.  I did experience an inability to make System > Preferences changes until I went: sudo chown -R bigbadsi /home/bigbadsi

I installed the Nvidia drivers using this guide [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29). I installed Gdesklets using Automatix.

The only /etc/X11/xorg.conf hack I've applied is to get my forward and back mouse buttons to work in Swiftfox by following [http://ubuntuforums.org/showthread.php?t=219894&highlight=MX500](http://ubuntuforums.org/showthread.php?t=219894&highlight=MX500).

Any help would be appreciated.

---

### Post by wisemanleo on 2007-12-30
Did you ever manage to solve this?

I have a similar problem. Compiz-fusion works great when its running, but I can't seem to figure out which keyboard layout is the right one. At first I thought it was 101 generic US, but that only worked until I restarted X. After restarting, the compiz key shortcuts stopped working again. I'd have to change the keyboard layout again to w/e else, be it 101 again or 105, as long as its changed, the shortcuts work again. 

What the hell?

---

