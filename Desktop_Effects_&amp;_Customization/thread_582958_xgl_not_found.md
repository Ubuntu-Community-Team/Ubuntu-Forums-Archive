---
title: "xgl not found"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by jtouso on 2007-10-20
Hi!!
Ubuntu 7.10 live-mode, Ati-Radeon 9550 agp graphic chart. When type glxinfo it says Direct Rendering yes. My xorg.conf has composite enable, the driver is ati (free from xorg).
I also look for libgl1-mesa-dri and glx and also for xserver-xorg-video-ati. All is ok but..I can not use compiz!!!
If I type in terminal as root compiz it answer Xgl not found.
What is happen?
Thanks 
Jose

---

### Post by Stemp on 2007-10-20
compiz as root ? why ? 

try just this as user :
```
compiz --replace
```

---

