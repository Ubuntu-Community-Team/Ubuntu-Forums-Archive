---
title: "supertuxkart won't start"
date: 2011-10-16
forum: Gaming &amp; Leisure
---

### Post by maleicon on 2011-10-16
hi

on fresh install of ubuntu 11.10 supertuxkart won't start

```
NIrrlicht Engine version 1.7.2
Linux 3.0.0-12-generic-pae #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 i686
[FileManager] Data files will be fetched from: '/usr/share/games/supertuxkart/'
[IrrDriver] Creating NULL device
Irrlicht Engine version 1.7.2
Linux 3.0.0-12-generic-pae #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 i686
[IrrDriver] Trying OpenGL rendering.
[IrrDriver] Tring to create device with 32 bits
Xlib:  extension "GLX" missing on display ":0.0".
[IrrDriver Temp Logger] Level 1: No GLX support available. OpenGL driver will not work.
[IrrDriver Temp Logger] Level 2: Fatal error, could not get visual.
Segmentation fault
```

thanks for any ideas about it.

---

### Post by Perfect Storm on 2011-10-16
Which video card do you have? Have you checked if any 'additional driver' is available?

---

### Post by maleicon on 2011-10-16
the card is nvidia GT 420M

additional driver nvidia version current is available. it's activated and in use. but only integrated intel card seems to be recognised by the system. nvidia settings give me information that i don't use it. 

i've been all over the internet trying to solve it but failed.
i've read that nvidia don't support optimus technology on linux.

on mint 11 it's not in use and supertuxkart also won't start.

however supertux worked in previous ubuntu.

---

### Post by Perfect Storm on 2011-10-16
Try disable the intel card in BIOS. It may conflict.

---

### Post by maleicon on 2011-10-16
Unfortunately there is no option to disable it in BIOS.

---

### Post by Perfect Storm on 2011-10-16
> **maleicon said:**
> Unfortunately there is no option to disable it in BIOS.

I think you should take your video card issues over at our other forum: [http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332) as you can't use this game without a decent video card and driver.

Though you could try to configure Xorg to use the Nvidia card:
```
sudo Xorg -configure
```

---

