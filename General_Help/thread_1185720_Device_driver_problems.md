---
title: "Device driver problems"
date: 2009-06-12
forum: General Help
---

### Post by papabill on 2009-06-12
I just installed Ubuntu 8.04-1 on a machine, and the video and audio are not working properly. The video will not reach it's fullest resolution, and I cannot make the audio what it's supposed to.

I have the motherboard support CD with all the windoze drivers on it, but don't know how to use them to work in Linux.

Any advise or suggestions.

Thanks

---

### Post by prem1er on 2009-06-12
Select System > Administration > Restricted Drivers Mangager

See if you can enable any drivers for your card. Also post the output of...

```
lspci
```

---

### Post by papabill on 2009-06-12
There is no System > Administration > Restricted Drivers Mangager.
The closest thing I have is System > Administration > Hardware Drivers, and all it tells me is that there are "No proprietary drivers are in use on this system"  

The audio works, but I cannot get the video resolution to the full 1280x1024 that it used under windoze.

bill@Ubuntu:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 761/M761 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA (rev 01)
00:0d.0 Communication controller: Agere Systems Unknown device 0620
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)

---

### Post by synapsys on 2009-06-12
```
sudo apt-get install ubuntu-restricted-extras
reboot
```

---

### Post by gradinaruvasile on 2009-06-12
The windows drivers wont help.


Try
sudo dpkg-reconfigure -phigh xserver-xorg

for the video. Then reboot.
What resolution u have?

You could try booting with a 9.04 live cd to see if its better (newer drivers etc).

---

### Post by papabill on 2009-06-12
Highest resolution I can get it 960x600. It's a 17" standard (old-style) monitor, so everything is so big, the dialog screens will not all fit in the screen.

I get a warning: 
dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20090612194013

---

### Post by papabill on 2009-06-12
> **synapsys said:**
> ```
sudo apt-get install ubuntu-restricted-extras
reboot
```

Nope, all that, and no change.

---

