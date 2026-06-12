---
title: "Cannot start compiz with ATI Radeon Mobility HD 3650"
date: 2009-05-01
forum: General Help
---

### Post by binarycortex on 2009-05-01
I am using wubi on an HP EliteBook 8530p it has an ATI Mobility Radeon 3650.

Here is the output from compiz-check

```
Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Mobility Radeon HD 3650
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use
```

this is the automatically generated Xorg.conf
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

```
lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3650 [1002:9591]
```

I tried this and it didnt work.
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by Legace on 2009-05-01
Check FGLRX driver status under SYSTEM > ADMINISTRATION > HARDWARE DRIVERS.
Make sure the driver is activated..

-----

If you have problems after the installation of the FGLRX driver, then follow these steps:
Reboot PC, select "recovery mode" in boot-manager (GRUB) and then go for "root shell" option.
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```


then type
```
exit
```

---

### Post by prem1er on 2009-05-01
Haven't tried compiz yet, but I have the same card, so I figure I will run into this problem sooner or later.  Thanks.

---

### Post by binarycortex on 2009-05-02
> **Legace said:**
> Check FGLRX driver status under SYSTEM > ADMINISTRATION > HARDWARE DRIVERS.
Make sure the driver is activated..


Thanks for the get out of reinstall free card. Every time I try to install fglrx my video stops working. 

How do I make sure it's activated. I tried ```
sudo aticonfig --initial
``` but that didn't do it. How do I get these stupid drivers to work?

---

