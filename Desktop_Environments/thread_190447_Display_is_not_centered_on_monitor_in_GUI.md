---
title: "Display is not centered on monitor in GUI"
date: 2006-06-06
forum: Desktop Environments
---

### Post by jprez1980 on 2006-06-06
Hello,

Just recently installed Ubuntu and notcied something odd right away.  Irregardless of the resolution used the screen is never centered on my monitor.  It is always off to the right a good inch or so.  In command line mode the screen is fine, only in the GUI does it have this anomoly.  How do I go about correcting this issue?  I would imagine its a config issue with X windows but not for certain.

Thanks!
JP

---

### Post by txinga on 2006-06-06
I always have to adjust the monitor itself. Using the monitor's  wider/narrower/taller/shorter left/right/up/down controls. I don't think it's necessarily an Ubuntu specific problem. Happens on the machines here at work (Win2K, XP) all the time on a new install and we ghost everything.

---

### Post by jprez1980 on 2006-06-06
Wow that was a fast reply =)  I actually tried that (adjusting the monitor itself)...when I then use command line the screen is too far to the left and everything is cut-off.  I tried the same thing with another monitor a 17 inch and it had the same issue.  Not sure if its a video card driver issue or something specific to Ubuntu.  The monitor that belongs with this computer is a 21" Nokia hooked to a NVidia GeForce II video card.  Using FreeBSD and KDE or Windows never ran into this issue.  Sounds like its something I may have to deal with.

---

### Post by jprez1980 on 2006-06-07
Actually, I have figured out why this is occuring but not sure how to fix it.  I need to have an option for 60 Hz on the refresh rate.  The lowest number I have is 65 Hz.  How do I go about changing this?

Thanks!

---

### Post by rajko on 2006-06-07
hi
if your monitor is not centered od GUI desktop you need to adjust modeline in your /etc/X11/xorg.config file.
It's is probeable for another monitor...
there is a program which can generate modeline.

try xvidtune from desktop

---

