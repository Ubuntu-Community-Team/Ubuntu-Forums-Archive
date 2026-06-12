---
title: "resolution problem"
date: 2005-05-24
forum: Desktop Environments
---

### Post by tarun86 on 2005-05-24
i have installed Kubuntu a few days back and i am facing the resolution problem .I am not able to change the resolution from 640 x 480 to another.i have tried configuring xorgconfig but nothing helped
does kubuntu supports INTEL P4 82845 chipset???please help me


my chipset is:
Name	Intel(R) 82845G/GL/GE/PE/GV Graphics Controller
PNP Device ID	PCI\VEN_8086&DEV_2562&SUBSYS_4C598086&REV_01\3&267A616A&0&10
Adapter Type	Intel(R) 82845G Graphics Controller, Intel Corporation compatible
Adapter Description	Intel(R) 82845G/GL/GE/PE/GV Graphics Controller
Adapter RAM	64.00 MB (67,108,864 bytes)


and my monitor is 17'' LG

---

### Post by ZeroA4 on 2005-05-24
It would help if you post your /etc/X11/xorg.conf

But anyway you should check if:

- Section "Device" driver refers to the chipset of your card as oposed to be using some generic driver as: vesa, fbdev, svga this sort of things

- in Section "Monitor" and Section "Screen" you can comment out the lines that sets resolutions and frequencies, modern X should be able to get that dinamicaly
for example those sections on my xorg.conf:```
Section "Device"
	Identifier	"NVIDIA Corporation NV36 [GeForce FX 5700 LE]"
	Driver	"nvidia"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV36 [GeForce FX 5700 LE]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection
```you can edit the  /etc/X11/xorg.conf file by typing on a terminal:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
```Sorry for my poor english.

---

### Post by logan2004 on 2005-05-24
please paste your /etc/X11/xorg.conf

---

