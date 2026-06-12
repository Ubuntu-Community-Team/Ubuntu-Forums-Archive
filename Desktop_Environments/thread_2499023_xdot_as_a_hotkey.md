---
title: "xdot as a hotkey"
date: 2024-07-08
forum: Desktop Environments
---

### Post by ant2ne on 2024-07-08
Ive written an xdot script that moves a window to another monitor and manipulates the window size. It works flawlessly. I tried to bind the script to an ubuntu hotkey (settings - keyboard - custom) which sometimes works, but mostly doesn't. It will move the window without resize, or resize without move, or something complete different. The cnlt + L key is bound to "/path/to/my/script.sh argument" What could be possible causes for this?

ubuntu 24.04

Thanks

---

### Post by TheFu on 2024-07-08
hotkeys are controlled by the WM, Window Manager.  Which WM is being used?  Follow the methods that WM requires to configure hotkeys and it should work 100%.

I use xdotool for moving and resizing application windows. For example, 
```
#!/bin/bash

# Change to workspace 2
/usr/bin/xdotool   set_desktop_viewport 1980 0
sleep .2s;

# move Firefox to a specific place and size
/usr/bin/xdotool   search --name "Mozilla Firefox" windowmove 170  0
/usr/bin/xdotool  search --name "Mozilla Firefox" windowsize 1600  815
```

**xdotool** is for xorg/X11 display servers.  If you use Wayland, check out **ydotool**.

I'll check out xdot.  After a quick look, not something I need.  I use xdotool for all sorts of things.  Launching programs doesn't need it with my WM, but every WM is a little different.  If you are using Gnome as a DE, I cannot help. I've never used it.  I can only suggest reading the *Ubuntu Desktop Guide* manual for that. [https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)

---

### Post by ant2ne on 2024-07-08
I believe it is wayland. Interesting that xdotool works in just the script, but not as a hotkey/script combo. I will take a look at ydotool. Thanks

---

### Post by TheFu on 2024-07-08
> **ant2ne said:**
> I believe it is wayland. Interesting that xdotool works in just the script, but not as a hotkey/script combo. I will take a look at ydotool. Thanks

xdotool doesn't work with wayland. Use ydotool instead. I don't know if they use the same options and I'm positive that ydotool doesn't have all the features of xdotool.

It isn't a script issue.  It is something in your WM.  That's where I'd start.

---

### Post by vanadium on 2024-07-09
ydotool is limited to input simulation - keyboard and mouse. It cannot manipulate windows. This is because the way windows are manipulated depends on the Wayland compositor. It is totally different between wlroots, mutter (Gnome) or KDE. You depend on your wayland compositor exposing a command line interface to manipulate windows using scripts. For Gnome, either the security must be turned off or third party Gnome Shell extensions are required to expose command line interfaces.

Classical tools for xorg will still work on Wayland for these "legacy" applications that run on Xorg through XWayland. You can tell which applications run on XWayland with `wmctrl -l`. Only programs on Xorg will be listed here. If the list is empty, then it means that everything is running natively on Wayland.

I have no clue about that xdot script, so I cannot have a clue as to why it sometimes works, sometimes not. There may be a need to insert a small pause in the script to make it work more reliably.

---

