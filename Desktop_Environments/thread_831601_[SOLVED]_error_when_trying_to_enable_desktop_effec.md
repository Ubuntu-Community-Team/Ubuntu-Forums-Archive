---
title: "[SOLVED] error when trying to enable desktop effects"
date: 2008-06-17
forum: Desktop Environments
---

### Post by Ryklou on 2008-06-17
ok i have been trying this for like 4 day's now and i still dont know what's wrong. When i try to activate the visual effect's it say's that it cant enable desktop effect's.  It made me install the video driver already. idk what the problem is. if there is anybody else out there that can help me please help me :KS TNX!

[URL="http://i110.photobucket.com/albums/n109/Ryklou/SCRENNSHOTS/hlp1-3.png"]
[IMG]http://i110.photobucket.com/albums/n109/Ryklou/SCRENNSHOTS/hlp1-1.png[/IMG][/URL]
Click on image to get bigger image.


[FONT="Courier New"][SIZE="3"]~francois[/SIZE][/FONT]

---

### Post by Ryklou on 2008-06-17
```
francois@ShadowGFX-Linux-CPU:~$ ./compiz-check

Gathering information about your system...

 Distribution:          **Ubuntu 8.04**
 Desktop environment:   **GNOME**
 Graphics chip:        ** nVidia Corporation NV34 [GeForce FX 5200] (rev a1)**
 Driver in use:         **nv**
 Rendering method:      **AIGLX**

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ [COLOR="Lime"]OK[/COLOR] ]
 Checking for non power of two support...          [ [COLOR="Lime"]OK[/COLOR] ]
 Checking for composite extension...               [ [COLOR="Lime"]OK [/COLOR]]
 Checking for FBConfig...                          [ [COLOR="Lime"]OK[/COLOR] ]
 Checking for hardware/setup problems...           [[COLOR="Red"]FAIL[/COLOR]]

There has been (at least) one error detected with your setup:
 [COLOR="DarkRed"]Error:[/COLOR] nv driver in use 

Would you like to know more? (Y/n) Y

 The nv driver is not capable of running Compiz, you need to install the
 latest nouveau or the proprietary nvidia driver 
```
[FONT="Courier New"]
ok did more reaserch and this is what i saw. is this the problem if so how do i fix it?[/FONT]

---

### Post by rainwalker on 2008-06-17
Run ```
SKIP_CHECKS=yes compiz
``` and see what it tells you. 

EDIT: Ah, I see you already found the compiz-check script :)
I don't really know what to tell you...

---

### Post by Ryklou on 2008-06-17
ok nvm. i found out that if you install the right driver then log out/in then you will have a nasty looking (lol big screen) and i dont like that. thanks anyway.

---

