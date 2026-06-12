---
title: "Wine is too slow"
date: 2006-03-30
forum: Gaming &amp; Leisure
---

### Post by mads-b on 2006-03-30
So, I've followed a howto on linux-gamers.net, setup steam, hl2 and so on. Problem is, as I fire up the game with the following command:
WINDEBUG=-all wine /mnt/hdb/games/Steam.exe -fullscreen -width 800 -height 600 -applaunch 220 -heapsize 256000 +map_background none "$@"
It takes an eternity to fire up, rendering everything useless, as it takes 15 seconds to respond to my clicks, and lags with 0,5 fps. What have I done wrong? What's the performance loss in wine compared to winXP?

Hardware below, for those interested: (I know it sucks, but it was more than enough in win.) 
MSI KT6V
AMD athlon XP 1900+
Nvidia Geforce FX5200
2x TwinMos 256MB RAM unknown clock. 
Two IDE disks with 6 and 200GB


Thanks in advance for your help

---

### Post by Perfect Storm on 2006-03-30
I'm not much into wine but what about an **-opengl**

---

### Post by R3linquish3r on 2006-03-30
you need to enable 3D Hardware excelleration

---

### Post by mads-b on 2006-03-30
How do I do that? I'm a complete noob at this. Someone have a howto or a complete tweaking guide?

---

### Post by Perfect Storm on 2006-03-30
```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```

reboot

---

### Post by mads-b on 2006-03-30
```
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

```
Error?
```

Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

```
Relevant stuff in the xorg file. What's wrong?

---

### Post by LordBug on 2006-03-31
The errors stem from someone (I'm guessing you?) manually editting the xorg.conf file. The Modules and Video section you listed should enable full nVidia 3D.  Might want to check framerates in glxgears (run from a console!) and see what you get.

---

