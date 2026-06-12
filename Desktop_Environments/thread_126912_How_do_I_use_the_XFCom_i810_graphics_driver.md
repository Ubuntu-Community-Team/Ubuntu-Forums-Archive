---
title: "How do I use the XFCom_i810 graphics driver"
date: 2006-02-07
forum: Desktop Environments
---

### Post by spitfireNoob on 2006-02-07
Hello, I've only recently installed 5.10 on an old Dell Opteron P3 933MHz, and OK so far. but I tried Eternal Lands, and it freezes. Looks like I haven't got accelerated graphics going:

> glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI

The PC uses the Intel 82810 on board graphics, so I got the driver which I downloaded from Intel as an RPM (the only option). I used synaptic to install 'alien' which then installed it for me with a 'sudo alien -i XFCom_i810-1.2-3.i386.rpm' command, and now I have these files in my /usr/X11R6/bin directory (the top one looks new):

-rwxr-xr-x  1 root root 2524320 2000-05-22 20:48 XFCom_i810
-rwxr-xr-x  1 root root 1790168 2005-10-10 19:10 Xorg
-rwsr-sr-x  1 root root    7508 2005-10-10 19:10 X
-rwxr-xr-x  1 root root    4648 2005-10-10 19:10 mmapw
-rwxr-xr-x  1 root root    5100 2005-10-10 19:10 mmapr
-rwxr-xr-x  1 root root    9184 2005-10-10 19:10 ioport
-rwxr-xr-x  1 root root    7952 2005-10-10 19:10 gtf

So my question is, how do I actually get this driver loaded and running?

Any help very much appreciated!

---

### Post by Vytas on 2006-02-24
i810 graphics driver is provided with your X.org version, check X.org config if the card is listed correctly (driver should be ***i810***), also check if DRI, GLX are enabled.

P.S. Dont expect much from this onboard chipset, you will have a low/very low framerate (~5-15 fps) in Eternal Lands, even if you sort your problems out. Also, there is a bug in i810 drivers and most likely you will have artifacts/missing textures in EL. This EL patch might help: [http://developer.berlios.de/patch/?func=detailpatch&patch_id=835&group_id=1256](http://developer.berlios.de/patch/?func=detailpatch&patch_id=835&group_id=1256)


Edit: AFAIK oldest i810 cards provide acceleration only in 16 bits/pixel, check that out too

---

