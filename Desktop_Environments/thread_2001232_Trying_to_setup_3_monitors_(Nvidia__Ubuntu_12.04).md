---
title: "Trying to setup 3 monitors (Nvidia / Ubuntu 12.04)"
date: 2012-06-10
forum: Desktop Environments
---

### Post by N3v on 2012-06-10
Okay, I have two video cards - a Geforce GTX 460 SE and a Geforce 8400 GS, both of which show up in nvidia-settings.

After enabling the other two monitors in nvidia-settings, they still didn't show up in system settings->displays until I went back into nvidia-settings and enabled xinerama.  Now I get an ouput to each monitor but I have some problems:

1. I need one monitor to be rotated upside down, and after enabling xinerama xrandr no longer works, when I type it into terminal it gives me "RandR extension missing"  I have tried editing xorg.conf manually, I can rotate it clockwise and counterclockwise but not upside down with the following:

Option "RandRotate" "on"
Option "Rotate" "CCW" #or "CW" both work, but "UD" for upside down does not

Any suggestions?

EDIT: The next two problems were solved by switching to Gnome

Thanks!

---

