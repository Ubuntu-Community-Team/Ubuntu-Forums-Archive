---
title: "Downgrading ATi FGLRX driver"
date: 2008-12-02
forum: Desktop Environments
---

### Post by cybernet on 2008-12-02
```
This driver is required to fully utilise the 3D potential of some ATI graphics cards, as well as provide 2D acceleration of newer cards.
```
[http://img505.imageshack.us/img505/1954/screenshothardwaredrivexz3.png](http://img505.imageshack.us/img505/1954/screenshothardwaredrivexz3.png)

Ubuntu 8.10 - ATI Sapphire  1650 PRO 512 MB

I didn't install this but if i will  and after reboot it gives a error about
x.org server, how can i make the downgrade to what it was :confused::-s

---

### Post by r m h on 2008-12-12
I just went through this tonight - I built a new super workstation last night (ASUS Rampage II Extreme mobo, 12GB RAM, an Intel Core i7 2.94GHz CPU (seen as an 8 CPU 47037.85 BogoMIPS system), dual Radeon HD4850 dual DVI video cards, 3Ware 9650SE with a 6 250GB SATA II RAID array), and installed Intrepid Ibex on it today.  Everything was great until I "upgraded" to the proprietary AMD/ATI FGLRX drivers for my dual Radeon HD4850 video cards and *poof* no more X windows.  I kept getting failures like no device at PCI location.  

Even running the failsafe 'dpkg-reconfigure -phigh xserver-xorg' wouldn't recover it until I did the following:

I downgraded the fglrx driver (removed it) by doing the following:

Heavy-handed deletion of the fglrx module
# rmmod fglrx
# rm /lib/modules/2.6.27-9-generic/updates/dkms/fglrx.ko

Remove the artefacts (which is the actual cause of the inability to run X) from modules.alias:
edit /lib/modules/2.6.27-9-generic/modules.alias 
and remove all lines ending with 'fglrx' - there were quite a few of them in my modules.alias file and they were all at the very end of the file.

Reboot
# shutdow -r now

When Intrepid rebooted, the failsafe X recovery worked like a charm and *voila* I had X again.

So much for those damn proprietary drivers, regardless of how well intentioned the support may be.

YMMV

---

### Post by r m h on 2008-12-13
I have found a number of fixes for the problem of the ATI FGLRX Xserver issue.

My fix was to install the proprietary ATI/AMD FGLRX drivers and update my /etc/X11/xorg.conf file to the following:

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "EnableMonitor" "crt1,lvds,tv,tmds1,crt2,tmds2,cv,tmds2i"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection


I have an ATI HD4850 card in PCIbus 2:0:0.

There are certain combinations of x86_64, mainboards, and ATI cards when using 4+GB of RAM that require you to manually configure the MTRRs on your system.

See [http://ubuntuforums.org/showthread.php?p=6364262#post6364262]("http://ubuntuforums.org/showthread.php?p=6364262#post6364262") for details

---

