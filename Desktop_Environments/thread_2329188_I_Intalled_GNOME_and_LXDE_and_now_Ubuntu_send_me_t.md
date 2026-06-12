---
title: "I Intalled GNOME and LXDE and now Ubuntu send me to command line"
date: 2016-06-28
forum: Desktop Environments
---

### Post by pixi6 on 2016-06-28
Hi. I have been user of ubuntu for 1 year, today i was trying to install GNOME and LXDE and i succes, i restart the system but now it enter to command and not to the desktop enviroment, I removed GNOME and LXDE but still send me to command line, y start recovery mode and try ti fix package but it didint work. Somone know how to fix it? i will be very grateful.

I have ubuntu 15.04

Thanks.

---

### Post by Liam_Murphy on 2016-06-28
Firstly, somewhat unrelated, 15.04 is no longer supported. It lost support back in February/March I believe. 

So GNOME and LXDE are uninstalled now? Well of course that'll send you to the command line if you have no DE, unless I misunderstood.



Try typing in
```
gdm
``` for Gnome
```
lightdm
``` for LXDE
and/or ```
startx
```

If none work, post the errors related to each command.

---

