---
title: "Can't set hight resolution"
date: 2015-03-31
forum: Desktop Environments
---

### Post by sirio81 on 2015-03-31
The problem is that I have 16:9 monitor and the higher resolution I can set is 1024x768.

```

# This is my vga
00:02.0 VGA compatible controller: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02)

# This is my monitor
HP Compaq LA2206xc

# This is the output of xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA-0 connected primary 1024x768+0+0 (normal left inverted right x axis 
y axis) 0mm x 0mm
    1024x768       60.0*
    800x600        60.3     56.2
    848x480        60.0
    640x480        59.9
```

I tried also to create xorg.conf and set HorizSync and VertRefresh but I can't still set a higher resolution.
I'm running ubuntu 14.04.

What can I do?

Thank you.

---

### Post by dino99 on 2015-03-31
if you still have a xorg.conf file, then delete it; now the system directly deals with the hardware, and xorg.conf is mainly needed when dealing with multiple screens.
when you glance at logs, is the hardware (screen) correctly detected ?
maybe purge the driver then reinstall it

---

### Post by sirio81 on 2015-03-31
> if you still have a xorg.conf file, then delete it
Well, there wasn't a xorg file before and it was not working.
Deleting xorg is not going to help.

> when you glance at logs, is the hardware (screen) correctly detected ?
I guess not because in the ubuntu control panel it was showing "unknown monitor" (with and without the xorg.conf).
I'll report logs as soon as I can.


> maybe purge the driver then reinstall it
If it does, it should be inside the package xserver-xorg-video-intel.
I'll check if there's anything wrong with the package but I don't think reinstalling it will help.

I forgot to mention a note: I blocked the linux-image package version to avoid continuos updates.
The problem was present also before I blocked it.

---

### Post by Siddhartha_Kashyap on 2015-04-04
Maybe you should install driversGo to the dash > type in " Additional Drivers " >
Open tool called " Additional Drivers " > Select the
" recommended drivers " and install them .

---

### Post by sirio81 on 2015-09-25
I found an how to that fixes the problem:
[https://anhe51.wordpress.com/2012/01/30/change-resolution-of-unknown-monitor-in-ubuntu-11-10/](https://anhe51.wordpress.com/2012/01/30/change-resolution-of-unknown-monitor-in-ubuntu-11-10/)

Example:

```
cvt 1440 900
```
usign this output
```
xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr --addmode VGA1 1440x900_60.00
```
To fix this every time you reboot, generate an xorg.conf file and in the section montir add
```
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
```

---

