---
title: "Second monitor stuck sideways in 14.04.1 Unity"
date: 2015-02-12
forum: Desktop Environments
---

### Post by lukon on 2015-02-12
Second monitor stuck sideways in 14.04.1 Unity

Tried fixing this through System Settings > Displays

But the only options available for the Rotation option are “Counterclockwise” and “Clockwise.” No “Normal” option is available.

This second monitor is a SHARP X Flat TV.

The Displays setting utility names this second monitor as “Unknown Display.”

Clicking the “Detect Displays” button in the Displays setting utility changes nothing.

The signal for this second monitor is routed through a home theater receiver/amp before it reaches the TV.

The first monitor is a TOSHIBA TV/VGA Monitor thing and the Display settings utility names it specifically and correctly.

The computer is an HP Media Center PC m7250n desktop – dual boot Windows XP and Ubuntu 14.04.1. (Of course the dual monitor setup works perfectly in Windows XP.)

The video output is via a PCI video card.

So here is my lspci output:

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X300]
01:00.1 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X300 SE]
02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
02:03.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) Video Decoder (rev 01)
02:04.0 Mass storage controller: Promise Technology, Inc. 20269 (rev 02)
02:05.0 Communication controller: LSI Corporation 56k WinModem (rev 01)
02:08.0 Ethernet controller: Intel Corporation NM10/ICH7 Family LAN Controller (rev 01)

So, is there a way to get my second monitor normalized?

[P.S. Why did the Ubuntu folk design the second monitor function to output sideways only for unknown monitors? Like, wouldn't “Normal” have been a better default for that? Geeeeez.]

---

