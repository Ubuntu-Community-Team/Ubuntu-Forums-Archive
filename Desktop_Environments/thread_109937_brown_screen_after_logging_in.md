---
title: "brown screen after logging in"
date: 2005-12-29
forum: Desktop Environments
---

### Post by mikh84 on 2005-12-29
sorry i'm new at this but

i just installed ubuntu and i get a brown screen with just my mouse cursor.. i've tried dpkg-reconfigure xserver-xorg and i've looked in my umm.. xorg.log... theres like font render warnings and some other stuff lol :oops:

---

### Post by thekiller on 2005-12-29
can u post your xorg.conf here ?

---

### Post by mikh84 on 2005-12-29
umm well how do u that.. im on windows right now

---

### Post by tlc on 2005-12-29
Try this - edit your xorg.conf file...
```
sudo nano etc/X11/xorg.conf
```
Find the Device section and change the Driver "nv" to driver "vesa" 
Save and exit.
Restart X or reboot. 
Report back... hopefully you'll be able to log in OK. You can then go about installing the nvidia driver. If you have an ATI card then disregard all of the above. :razz:

---

### Post by mikh84 on 2005-12-29
[QUOTE=tlc]Try this - edit your xorg.conf file...
```
sudo nano etc/X11/xorg.conf
```
Find the Device section and change the Driver "nv" to driver "vesa" 
Save and exit.
Restart X or reboot. 
Report back... hopefully you'll be able to log in OK. You can then go about installing the nvidia driver. If you have an ATI card then disregard all of the above. :razz:[/QUOTE]
hey that worked - i have an nvidia card :smile: 

thanks everyone :smile:

---

