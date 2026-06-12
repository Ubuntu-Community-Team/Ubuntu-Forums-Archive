---
title: "nVidia &quot;gdm_slave_xioerror_handler:&quot; X.org crash (reproducible with Open Office)"
date: 2008-10-09
forum: Desktop Environments
---

### Post by thoughtbox on 2008-10-09
I'm experiencing reproducible X.org crashes on my Ubuntu 8.10 on a Lenovo T61p (nVidia M570 chipset).

If I load a document with Open Office and scroll around the document it will cause X to reload with a 'Oct  9 15:28:02 t61p gdm[22813]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0' in the Xorg.log file.

Before X reloads, there is a visible "NVRM:" line, so:

NVRM: Xid (0001:00): 13 0001 00000000 00005039 00000328 00000000 00000023

What is causing this? I am told this is "XRENDER", but I'm not sure how to turn this function off (I am using proprietary drivers) so I can try an eliminate (confirm) it.

Has anyone else experienced similar problems?

/TB

--
tb@t61p:~$ uname -a
Linux t61p 2.6.24-21-server #1 SMP Mon Aug 25 17:28:54 UTC 2008 x86_64 GNU/Linux

---

### Post by Remsiukas on 2008-10-09
Help me please ,assistance to me please,i'm a  world-weary,because me to take the knock,please help me.
my contact is [email]cigaras26@yahoo.com[/email]

---

### Post by alterego2 on 2008-11-05
Hi, thoughtbox,
did you find any soultion/bugfix?

I have same problem on Ubuntu 8.10 on a Lenovo T61p.

---

### Post by frodon on 2008-11-16
I'm experiencing this on my intrepid box.

I can reproduce it right clicking any gdeskelt or just playing with system monitor.

So far the only workaround i found is to activate metacity composite manager, once activated i can't reproduce the crash with gdesklet or system-monitor.

I have seen some user reporting than upgrading to latest nvidia drivers (for nvidia users) can solve such issues.

---

### Post by rantenki on 2008-12-07
Glad to see I am not the only one. I get the exact same behavior, but my entire box sometimes reboots. The reboot is sporadic, I would say one time in 5. It seems like the box needs to be up for a few days before it gets unstable enough to reboot spontaneously, although the Xorg crash seems to happen every couple of days. I see the exact same log messages as posted above. I also see:
> Dec  7 13:30:39 vader kernel: [348890.044785] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00000f10 00000000 00000040
Dec  7 13:30:39 vader kernel: [348894.143007] NVRM: Xid (0001:00): 55,  L1 -> L0
Dec  7 13:30:40 vader kernel: [348894.439414] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00000e08 00000000 00000040
Dec  7 13:30:40 vader kernel: [348894.439784] NVRM: Xid (0001:00): 55,  L1 -> L0
Dec  7 13:30:40 vader kernel: [348894.645542] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00000e08 00000000 00000040
Dec  7 13:30:40 vader kernel: [348894.646014] NVRM: Xid (0001:00): 55,  L1 -> L0
Dec  7 13:30:40 vader kernel: [348894.841558] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00000e08 00000000 00000040
Dec  7 13:30:40 vader kernel: [348894.841982] NVRM: Xid (0001:00): 55,  L1 -> L0
Dec  7 13:30:40 vader kernel: [348895.029926] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00000e08 00000000 00000040
Dec  7 13:30:40 vader kernel: [348895.030405] NVRM: Xid (0001:00): 55,  L1 -> L0
Interestingly, I don't need to play with gdesklets or anything like that; glmatrix the screensaver will trigger it too.

lspci:
> 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
07:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
08:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

System is an Asus G1S laptop with Core2 7500 and 2 Gigs of ram, on X86_32.

---

