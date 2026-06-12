---
title: "gdm freezes after login"
date: 2011-06-22
forum: Desktop Environments
---

### Post by d.block on 2011-06-22
Hello list,

After logging into my ubuntu (lucid), the system freezes. The whole screen is white colored or sometimes it loads the background image, but it doesn't show any items on the desktop and any panel. It also doesn't react on commands like [Alt]+[F2].

Switching to the terminal with [Ctrl]+[Alt]+[F1] is possible. I ran the command
```
top
```which shows a cpu usage of the gnome-panel around 100% the whole time.

I reinstalled gdm already many times, but it didn't have any effect. Also changing the settings with the command
```
gdmsetup
```didn't have any effect.

I didn't find a similar post in this forum, so can somebody help me? Does anybody have experiences with such problems?

Thank you in advance!

---

### Post by Krytarik on 2011-06-23
First, this has nothing to do with GDM at all, but instead one of these apps are crashing for some reason:
- "gnome-panel": missing panels; it also affects Alt+F2, as it is a feature of it
- "nautilus": missing desktop items, or white background

Both of those (not the white background, though) randomly happened to me on Lucid earlier when I didn't have this option in the "Screen" section of my "/etc/X11/xorg.conf" for the proprietary Nvidia driver:
```
Option         "AddARGBGLXVisuals" "True"
```It may also be a general issue with the video driver you are running.

And if you are running Natty 11.04, there seem to be some issues regarding the handling of the desktop by Nautilus.

One related bug report is here:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/786653](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/786653)

And related threads are here:
[http://ubuntuforums.org/showthread.php?t=1736604](http://ubuntuforums.org/showthread.php?t=1736604)
[http://ubuntuforums.org/showthread.php?t=1742697](http://ubuntuforums.org/showthread.php?t=1742697)

Also, to possibly get any further clues, check the log file "~/.xsession-errors".

Hope this helps!

---

