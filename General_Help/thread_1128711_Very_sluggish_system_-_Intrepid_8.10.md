---
title: "Very sluggish system - Intrepid 8.10"
date: 2009-04-17
forum: General Help
---

### Post by jermsie on 2009-04-17
My mother's ubuntu system is running quite sluggish I've found and I'm wondering what the cause of this would be and if there are some possible solutions?

Using 'sysinfo,' here are some details  on the setup:

Kernal: 2.6.27-11-generic
CPU: Intel(R) Celeron(R) CPU 2.40GHz
128 KB L2 cache
Memory: 512MB shared RAM
Hard drive: WDC WD400EB-11CP (ATA)

I've noticed that basic actions such a click on buttons in Nautilus, moving windows, and changing tabs (to name a few) are quite laggy with some of these actions taking 0.5 - 1second. CPU load gets quite high for these things as well which seems strange.

---

### Post by Mike_IronFist on 2009-04-18
> **jermsie said:**
> My mother's ubuntu system is running quite sluggish I've found and I'm wondering what the cause of this would be and if there are some possible solutions?

Using 'sysinfo,' here are some details  on the setup:

Kernal: 2.6.27-11-generic
CPU: Intel(R) Celeron(R) CPU 2.40GHz
128 KB L2 cache
Memory: 512MB shared RAM
Hard drive: WDC WD400EB-11CP (ATA)

I've noticed that basic actions such a click on buttons in Nautilus, moving windows, and changing tabs (to name a few) are quite laggy with some of these actions taking 0.5 - 1second. CPU load gets quite high for these things as well which seems strange.

Please give us the lowdown on your graphics card. If you are running an old graphics card driver, that might be the problem.

---

### Post by jermsie on 2009-04-18
> **Mike_IronFist said:**
> Please give us the lowdown on your graphics card. If you are running an old graphics card driver, that might be the problem.

here's the result of the lspci command

```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter


```

---

### Post by jermsie on 2009-04-19
Please guys, if anyone can help. I don't have much time to fix the problem

---

### Post by disco41 on 2009-04-19
If you have graphics built in on Mobo then i think you need more system RAM 
Try running system monitor whilst doing things and see what usage the ram gets.
HTH  ;)

---

### Post by pbpersson on 2009-04-19
when you notice all the CPU usage, do you also see lots of disk activity?

Have you tried rebuilding your swap space?  It could possibly be corrupted.

---

### Post by ddrichardson on 2009-04-19
Is it using the right Xorg server? It should probably be xserver-*xorg*-video-[I]sis but might be using the generic vesa or SVGA server. Can you post your /etc/X11/xorg.conf
[/I]

---

### Post by jermsie on 2009-04-22
> **ddrichardson said:**
> Is it using the right Xorg server? It should probably be xserver-*xorg*-video-[I]sis but might be using the generic vesa or SVGA server. Can you post your /etc/X11/xorg.conf
[/I]

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

Note: now running 9.04 rc1. issue still stands

---

