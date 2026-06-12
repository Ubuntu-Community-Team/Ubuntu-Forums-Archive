---
title: "New Video Card Kills Wifi connection...?"
date: 2009-11-03
forum: Gaming &amp; Leisure
---

### Post by dacci on 2009-11-03
Ok. Im going to state the whole newb speal. I starting using ubuntu about 2-months back. I've always been a windows user, and hated it. I love ubuntu, especially when I figured out I could play WoW with wine. I decided to get a new video card, because ive been using the IGP on my mobo. I bought a new Radeon HD5770. At installation i see a box on the bottom right corner of the screen with an AMD logo saying unsupported hardware, but everything works fine. Here is where it gets wierd. When I fire up WoW, everything runs as expected, but i immediately lose my wireless connection. When i close it out. It automatically reconnects. What the heck could cause this. Is it a hardware conflict or software. I use a Linksys pci wireless adapter if that helps.

---

### Post by joeelmex on 2009-11-03
what drivers did you use to install the video card?  What version of Ubuntu are you running?  Type of system you have or list lspci for some help.

---

### Post by dacci on 2009-11-03
Im using the same ATI proprietary drivers that my IGP used. Which im sure is wrong. but when i searched for drivers thats what came up. My system specs are in my sig. Im not at home now to do the list lspci. Im guess that will have to be done in terminal...
 
I checked the ATI site, there are drivers for the 5800 series, which are based off of the same core as the 5700 series, but there isnt a specific driver yet for my card. I downloaded teh ATI catalyst 9.10, but when I follow the directions to install (its a .run file) nothing happens...

---

### Post by dacci on 2009-11-03
here is what i get with lspci:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68b8
01:00.1 Audio device: ATI Technologies Inc Device aa58
02:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403
04:05.0 Network controller: RaLink RT2561/RT61 802.11g PCI

---

