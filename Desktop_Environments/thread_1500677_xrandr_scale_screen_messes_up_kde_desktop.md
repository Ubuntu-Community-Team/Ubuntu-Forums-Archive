---
title: "xrandr scale screen messes up kde desktop"
date: 2010-06-03
forum: Desktop Environments
---

### Post by josvanr on 2010-06-03
In ubuntu I use xrandr to increase the resolution of my small 
laptop screen. 

xrandr --output LVDS1 --mode 1280x800 --scale 1.5x1.5

this is nice for applications that have large windows, like gimp.
I just downloaded the latest kubuntu (lucid lynx) and tried
this but it kind of messes up the desktop (see attatchment). Part
of the screen is black. Any ideas on how to resolve this?

josvanr

---

### Post by maestrobwh1 on 2010-10-20
Bump... I have this issue now and have checked here and on kubuntu forums and I am unable to fix it or get an answer if it is even "fixable."  Th command works in all desktops (gnome, lxde, fluxbox) but not kde.

---

### Post by Zorael on 2010-10-20
I'd suggest you file a bug over at the [KDE bugtracker](http://bugs.kde.org). Perhaps it's just a use-case the developers haven't thought of. If you do, please reply to this post with the bug number.

I tried the command on my laptop but it flat-out refused. Then again I use the proprietary nvidia driver.
```
$ xrandr --output default --mode 1680x1050 --scale 1.5x1.5
xrandr: Failed to get size of gamma for output default
xrandr: screen cannot be larger than 1680x1050 (desired size 2520x1575)
```

---

