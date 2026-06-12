---
title: "X session crash Lucid Lynx 10.04 Gnome using nvidia driver"
date: 2010-05-15
forum: Desktop Environments
---

### Post by andifink on 2010-05-15
I have a fresh install of Ubuntu 10.04 LTS (32bit) and get "unmotivated"
crashes of gnome/xserver using a GeForce 7300GS using the "nvidia current" driver
from the Ubuntu package (195.36.15) 
I know NVidia is providing a later one (195.36.24)

The only reporting about the crash I have found in Xorg.log
(segmentation fault) see attachment. In .xsession-errors I can not see any
reporting of the crash. the session just "drops" and the login screen appears
immediately.

I posted the bug to [https://bugs.freedesktop.org/show_bug.cgi?id=28113](https://bugs.freedesktop.org/show_bug.cgi?id=28113)
they say it is a driver issue...

Can you advise me to possibly get more logging info on the crash, maybe run the
xserver from a textconsole or enabling other debugging log info...?

Or where should I adress this?

Should I upgrade to latest NVidia driver 195.36.24?

---

