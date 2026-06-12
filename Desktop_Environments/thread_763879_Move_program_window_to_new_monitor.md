---
title: "Move program window to new monitor?"
date: 2008-04-23
forum: Desktop Environments
---

### Post by whein on 2008-04-23
I have two monitors set up for display, but I am not using Xinerama or TwinView, just the binary nVidia driver and some good old hacking in the xorg.conf file. All works well, I can move the mouse cursor between the two and launch a program on either by calling
```
DISPLAY=:0.0 foo.sh
```
or
```
DISPLAY=:0.1 foo.sh
```
as appropriate. However, I don't know how to move a program window between the monitors once it is already visible! I know for a single monitor with multiple desktops you can right click the window title (in Gnome and KDE) and it gives you the option to send the window to another desktop. Is there a similar functionality that would send it to another display/monitor? Seems like there really should be, but beats me how to do it! Any takers?

As an add on, is there a system call or something (preferably callable from Java without too much headache, I'm newish to Linux and know almost nothing about JNI...) that could be used to move windows to new displays?  Something in the X11 system I'm thinking?
-Will

---

### Post by kdb424 on 2009-05-14
I hate to necropost, but I am also wondering the same thing. Looking at what was done in the first post, it's twinview, and I am also wondering if this will ever happen. I do not think it will be as easy, as it does not allow easy communication between pidgin and skype if they are on different monitors, so I believe it is much deeper, but could be done with some work. I think this is definitely something to look into ESPECIALLY if you have more than 2 monitors. Unfortunately, most people only have 1 monitor at a time.

---

