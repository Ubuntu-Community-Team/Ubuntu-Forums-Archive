---
title: "OpenGL causes major slowdown"
date: 2008-06-01
forum: Gaming &amp; Leisure
---

### Post by Muzer on 2008-06-01
I was trying to get FCEU working on my pretty poor PC (512MB RAM, NVIDIA GeForce 2 Ti with 64MB Video RAM, can't remember the processor offhand), but it was having massive slowdown problems. However, I then disabled OpenGL accelleration and it ran quickly without a hitch, with the added bonus of it displaying in the correct aspect ratio on my widescreen monitor. Why does OpenGL cause this slowdown for me?

---

### Post by pro003 on 2008-06-01
i believe your gpu doesn't support opengl... correct me if am wrong.

---

### Post by Muzer on 2008-06-01
I'm not sure, I think it does (at least it does on Windows), but it might be to do with the fact I only have the Ubuntu drivers installed. I've tried and failed many times through various sources (NVIDIA's site, repositories etc) to install the correct legacy drivers for it but it either does X's equivalent of a Blue Screen of Death on startup, or you actually can't configure them because the xorg.conf is different from what is described.



I'm running Kubuntu 8.04 (KDE4 edition) by the way, though I highly doubt it makes any difference at all

---

### Post by hessiess on 2008-06-01
If you dont have the drivers installed then OpenGL will be renderd by softwere. I dont know if the lagancy drivers even support 3D acselaration. Carnt you get a new GPU? even the cheepist new card would be infanatly better than a 2 series one.

---

### Post by DoktorSeven on 2008-06-01
The legacy drivers for nvidia certainly do support 3d, and should work just fine for your Geforce 2 for 3d OpenGL games.  You need to make sure you are using the "nvidia-glx-legacy" package and that X is properly configured to use those drivers.

---

### Post by Muzer on 2008-06-06
> **DoktorSeven said:**
> The legacy drivers for nvidia certainly do support 3d, and should work just fine for your Geforce 2 for 3d OpenGL games.  You need to make sure you are using the "nvidia-glx-legacy" package and that X is properly configured to use those drivers.

I've done that countless times, but the nvidia-xconfig package or whatever it's called errors without changing anything and manually configuring it causes a crash on restart.


The same thing happens when installing them from the NVIDIA website.


I'll try yet again now, it might be different. :/


EDIT: Now, it doesn't even get that far, I can't seem to install nvidia-xconfig and nvidia-glx-legacy at the same time :/
EDIT2: Installing nvidia-xconfig and trying to run it errors as before:
[email]muzer@muzer-desktop:~/.wine[/email]/drive_c/windows/system32$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Segmentation fault
[email]muzer@muzer-desktop:~/.wine[/email]/drive_c/windows/system32$

---

### Post by Muzer on 2008-06-06
OK, I just did it and restarted X, and I'm getting the same that happened last time (I didn't mention it because it was unimportant):

The resolution is stuck on something ****, I'm guessing 640x480, maybe even 800x600.

Now if I restart the whole PC I am 99% sure it will crash.

---

### Post by Muzer on 2008-06-06
OK, it doesn't crash, but I'm still stuck with a **** resolution.

---

### Post by xeth_delta on 2008-06-06
> **Muzer said:**
> I was trying to get FCEU working on my pretty poor PC (512MB RAM, NVIDIA GeForce 2 Ti with 64MB Video RAM, can't remember the processor offhand), but it was having massive slowdown problems. However, I then disabled OpenGL accelleration and it ran quickly without a hitch, with the added bonus of it displaying in the correct aspect ratio on my widescreen monitor. Why does OpenGL cause this slowdown for me?

OpenGL is supported, and the slowdown is not due to the outdated card, most likely. A few years ago I got 3d acceleration working properly on an even older/slower nvidia card, a GeForce2 GTS.

How did you install the proprietary drivers?

---

### Post by Muzer on 2008-06-06
I got the nvidia-glx-legacy package from the repo, then manually configured X by changing:
```

Section "Device"
	Identifier	"nVidia Corporation NV15DDR [GeForce2 Ti]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

```
to:
```

Section "Device"
	Identifier	"nVidia Corporation NV15DDR [GeForce2 Ti]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

```.

I changed nothing else. Then, I restarted X with Ctrl+Alt+BS and got forced 800x600. Rebooting does the same.


Installing the legacy drivers from the NVIDIA site and manually configuring as before gives a BSOD with corrupted characters in it so I can't really read it on startup.

---

### Post by Muzer on 2008-06-06
OK, I got it working, I don't think the driver liked my monitor. Someone helped me over IRC.

---

