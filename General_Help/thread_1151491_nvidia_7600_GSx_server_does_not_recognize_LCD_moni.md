---
title: "nvidia 7600 GS/x server does not recognize LCD monitor"
date: 2009-05-07
forum: General Help
---

### Post by Cranders on 2009-05-07
Hello,  I have searched long and hard for a fix but I cannot find one that works.  I have a nvidia 7600 GS (I know it sucks) video card and a samsung syncmaster LCD monitor.  The problem is that Ubuntu does not recognize this monitor as a LCD, but as a CRT.  Because of this, I have limited resolutions.  I am not confined to very low resolutions, however I would like to have 1280x1024, which is not listed.  

When I have my LCD monitor and a actual CRT monitor connected, Ubuntu still recognizes them both as CRTs, however the actual CRT displays the monitor name and model.

Any ideas would help.  I have looked over several other posts, however I cannot find a fix.  I have the latest nvidia 180 driver installed.

---

### Post by KhurramM on 2009-05-07
Try out:

[http://www.linux-drivers.org/](http://www.linux-drivers.org/)

hope it helps u....

---

### Post by Cranders on 2009-05-07
Here is a copy of my xorg file with both monitors active.



Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

