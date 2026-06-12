---
title: "Sound does not work on my inspiron 1721 notebook after installing Kubuntu Hardy 8.04"
date: 2008-08-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dreamscaper on 2008-08-04
I have tried just about everything!

The computer is an inspiron 1721 notebook running Kubuntu Hardy Heron 8.04 and KDE 3.5.9. Specs are 17" widescreen monitor, 120 Gb hard drive, CD/DVD burner, ATI Radeon X1200 series video (128mb shared), 2 Gb ram, SB600 ATI audio card, AMD Turion64 X2 CPU,Broadcom BCM2405 Bluetooth, Broadcom 1390 mini-PCI wireless card, Broadcom ethernet, &#8206;Ricoh &#8206;SD Card reader, OmniVision Technologies, Inc. -2640-07.05.16.3 Integrated Webcam.

Here is my lspci:
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

Here is an article where someone else got their inspiron 1721 to work with a different distro: [http://pclinuxoshwdb.com/index.php?option=com_content&task=view&id=887&Itemid=63](http://pclinuxoshwdb.com/index.php?option=com_content&task=view&id=887&Itemid=63)

I have already tried acpi=off and it made it crash upon booting. As you can see from above, Kubuntu recognizes the card and has a driver for it, but nothing seems to make it produce any sound. My volume is all the way up, and it is not muted. The sound works fine in vista (this is dual boot). I looked on the alsa website and I couldn't even find the card listed there. What can I do to fix this?

---

### Post by bobdole211 on 2008-11-10
I also have the Inspiron 1721.

I often switch between Vista, Debian and Ubuntu.  I find that when using Debian or Ubuntu I have to download the alsa-source file (You'll have to grep/search for it, I have Vista installed at the moment) then build the program using:

m-a update
m-a prepare
m-a a-i alsa

Granted you'll have to install module-assistant and the other things that this requires (kernel headers, etc.), but this tends to get the sound working for me.

Hope this helps!  Might be a moot point now that 8.10 is out.  Haven't tried that yet myself.

---

