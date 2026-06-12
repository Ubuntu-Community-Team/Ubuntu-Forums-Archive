---
title: "Ubuntu 8.10 random freeze"
date: 2009-03-23
forum: General Help
---

### Post by marcoski on 2009-03-23
Hi all,
I had this problem since i've been install ubuntu 7.10. I hoped that 8.04 and 8.10 released fixed it but it wasn't. 

The problem is a completely and randomly systems freeze. No response to input (ctrl+alt+backspace, mouse lockup, keyboard lockup too), No network response (no ping, no ssh, no telnet), the only suck way i have is to hard reset my PC. Sometimes when system crash caps lock and caps num blink up (kernel panic)
I notice that such problem rise up especially when i play music (i notice with Amarok, Exile, RithmBox), or when i play a video (i notice with Totem, Xine, Vlc), or when i play video on Youtube or when firefox use flash player. Also i notice that my systems hangs up when i tried to transfer a big amount of data from device to device. It could be an external device, a network device or an internal device. In general system freeze when it handle a large amount of data.

I try to google the problem but none discussion solved my problem.

Initially I suspected an hardware problem so I did memtest for hours and hours, I tried to change my Nvidia card with an older ATI card, I did all disks test i know, such as badblocks, SMART test etc. But all my hardware seems to work fine good.

My hardware configuration is, from lspci:
[PHP]
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 LE] (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
05:00.0 FireWire (IEEE 1394): NEC Corporation uPD72873 IEEE1394 OHCI 1.1 2-port Host Controller (rev 01)
[/PHP]

My mobo is an asus P5K SE (bios firmware 0401), the SATA controller is Marvell 88SE6121 SATA II.
I got two RAM slot 1Gb each one.

My ubuntu is an 8.10 system with kernel 2.6.27-11-generic.

I don't use any wireless network card and my pc is a desktop PC, it's network plugged.

Someone can help me?

Thanks

---

### Post by utumno4 on 2009-03-24
If anyone has any feedback on this problem, it might help me out as well. I've installed ubuntu 8.10 on my server and my laptop, both of which seem susceptible to random freezing. It could be immediately after login, it could be hours later. 

I would suspect a hardware issue, and yet both machines have issues. Again, any advice would be welcome, having comps with a random reset timer ticking is very frustrating.

---

### Post by djay1991 on 2009-03-29
I also have this problem. It didn't start until after I upgraded my system. I am currently running an Asus M3A78-EM motherboard with an Athlon 7750, 2gb crucial ram, Radeon 4650. Help with this would be appreciated.

---

### Post by 5l4y3r on 2009-03-30
I also have this problem (except for the kernel panic part), but it use to happen  when I use Firefox.
It freezes the entire system and the only way out is to reboot my PC.

---

### Post by aaronLund on 2009-06-14
I have this same problem.

Here's my lspci:
```
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03)
05:0b.0 USB Controller: Silicon Image, Inc. USB0670 (rev 06)

```

I think it's something to do with either my soundcard or the nvidia driver.

---

### Post by ljyx123 on 2009-06-23
LOL so many problems yet no solutions so far

I also seem to have the same problem.
I'm currently using asus m3a78-em, ati x1900gt, athlon x2 7750BE, 2GB Patriot Viper Extreme ddr2-800 ram.

Any help would be greatly appreciated.
I think this has to do with Ati Drivers, as im also experiencing lock-ups on Windows XP when i run 3D games. The linux freezes are random, and as the poster said, also happens when i transfer large files.

Thanks in advance

---

