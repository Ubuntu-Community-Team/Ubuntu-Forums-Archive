---
title: "Fix for corrupted panel right-click background"
date: 2011-06-30
forum: Desktop Environments
---

### Post by opethfan89 on 2011-06-30
Hi all,

I was reading into a problem that I (and other users) were having regarding a messy-looking background menu when right clicking on the panel or otherwise. See bug report [here]("https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/711746").  In my novice way of tinkering around with things, I think I may have inadvertently "discovered" a very easy fix.

My steps:
1) ```
sudo gedit /usr/share/themes/Ambiance/gtk-2.0/apps/gnome-panel.rc
```2) Change "    bg_pixmap[NORMAL] = "img/panel.png"   to       bg_pixmap[NORMAL] = ""
3) killall gnome-panel
4) and voila!  This was done on an almost-vanilla Ubuntu 11.04 install (I installed maybe 2-3 days back)

I hope someone else can benefit from this fix!

- Opethfan89

*Edit* My guess, based on my rather limited knowledge, would be that you can fix the problem by changing the panel background to a solid color via the configuration GUI, or manually edit that .png file in the GIMP to remove the corruption, but that is just a theory.

---

