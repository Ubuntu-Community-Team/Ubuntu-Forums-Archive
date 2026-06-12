---
title: "can't get interface to start when graphics drivers are installed"
date: 2011-10-08
forum: Desktop Environments
---

### Post by emerald876 on 2011-10-08
I'm trying to install Ubuntu 11.04 on my custom build. Whenever I install the nvidia drivers, neither the gnome or unity interface starts. I have to go into terminal and type "gnome-panel --replace" 

If I uninstall the NVIDIA drivers, it goes into the gnome interface.

I'm just wondering if anyone could help me to figure out why it does this, it's the first time i've tried to install ubuntu other than a wubi on this build.


_**RIG**_
Phenom II x4 945
4GB DDR3 1333mhz (G.Skill)
NVIDIA GTS450

I'm not the most technical person when it comes to linux, so I might need alot of help doing simple tasks. 
Any help would be appreciated though.

---

### Post by Krytarik on 2011-10-08
Try adding this option to the "Screen" section of your "/etc/X11/xorg.conf", if it isn't there already:
```
Option         "AddARGBGLXVisuals" "True"
```
Hope this helps!

---

### Post by dFlyer on 2011-10-08
Don't know if this link will help you but you might want to give it a try:

[http://ubuntuforums.org/showthread.php?t=1647855](http://ubuntuforums.org/showthread.php?t=1647855)

---

### Post by emerald876 on 2011-10-08
UPDATE: I uninstalled them and installed the experimental 3D drivers and it works now, but i'm still not sure whether or not I should try and get the stable drivers.

---

### Post by Krytarik on 2011-10-08
> **emerald876 said:**
> I uninstalled them and installed the experimental 3D drivers and it works now, but i'm still not sure whether or not I should try and get the stable drivers.
Well, the open source "nouveau" driver with 3D support enabled - which is precisely what you are running now - , works good and stable enough, afaik. So, if it works for you, let it run. ;-)

---

