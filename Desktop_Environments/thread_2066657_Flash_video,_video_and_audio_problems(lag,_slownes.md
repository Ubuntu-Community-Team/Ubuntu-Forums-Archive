---
title: "Flash video, video and audio problems(lag, slowness) at AMD64 Ubuntu 12.04 32 bit"
date: 2012-10-05
forum: Desktop Environments
---

### Post by Cenko on 2012-10-05
Hello,

I have a amd64 desktop, which I've used gentoo and linux mint before, and did not have issues with audio. Since few months I have ubuntu 12.04(32 bit version), and have horrible multimedia experience. 

It's my work PC, so video + music is not a must have, but it starts to upset me when I want to listen to music, watch youtube once in a while.

My problems are:

1) Flash videos are not watchable, both audio and video are jumpy.
2) Downloaded videos(any format) and music lag once in a while, (it loops a specific part, like its a remix :)).

I have searched a lot and read the following threads, and tried suggestions but still the problems persist for me.
[http://ubuntuforums.org/showthread.php?t=1987116](http://ubuntuforums.org/showthread.php?t=1987116)
[http://ubuntuforums.org/showthread.php?t=1967025](http://ubuntuforums.org/showthread.php?t=1967025)
[http://ubuntuforums.org/showthread.php?t=1968972](http://ubuntuforums.org/showthread.php?t=1968972)

Can it be because I have 32 bit OS on 64 bit hardware? 

Here are some output that may help:

lspci
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780C [Radeon HD 3100]
3f:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
```

uname -a
```
Linux mybuntu 3.2.0-30-generic-pae #48-Ubuntu SMP Fri Aug 24 17:14:09 UTC 2012 i686 athlon i386 GNU/Linux
```

aptitude search flash |grep "i "
```
i A adobe-flash-properties-gtk      - GTK+ control panel for Adobe Flash Player
i   adobe-flashplugin               - Adobe Flash Player plugin version 11
```

I have the proprietart ATI driver for the graphics card.

---

