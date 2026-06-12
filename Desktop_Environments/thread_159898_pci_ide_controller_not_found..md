---
title: "pci ide controller not found."
date: 2006-04-13
forum: Desktop Environments
---

### Post by recklessray on 2006-04-13
hi, bit of a noob so go easy! ive fitted a pci raid card so i can houz more hard drives in my linux box (breezy 5.10). its found in the bios but linux doesnt seem to think it exists... anyone please show me a few commands to help locate / install or otherwise sort it out...?

many thanks if you can help :)

ray/

---

### Post by recklessray on 2006-04-13
here is what lspci says - it sees the 'dual channel pci raid card'  - how can i enable it???? cheers!



ray@lucy:~$ ls
ls           lsb_release  lshw         lsof         lspgpot      lsusb
lsattr       lshal        lsmod        lspci        lspnp
ray@lucy:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS 645xx (rev 02)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:0a.0 RAID bus controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (PCI version seems to be IT8212, embedded seems (rev 11)
0000:00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
ray@lucy:~$

---

