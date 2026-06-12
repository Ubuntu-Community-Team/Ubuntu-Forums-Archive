---
title: "Dell Latitude D630 - Two annoying problems"
date: 2008-10-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rickyjones on 2008-10-01
Hello,

I apologize in advance if this problem has been resolved before. I did a few searches but could not find anything specifically geared to my problems.

There are two main issues preventing me from consistently using Ubuntu as the primary OS on my laptop. 

1. When suspending/resuming it works about 90% of the time without issue. However it seems that once in a while when resuming it refuses to find any of my network connections - wired or wireless - it looks like it just loses any and all information on my hardware. The solution has been to reboot, but I don't believe this is elegant or a good thing. It appears that all other necessary hardware works, however. Just network related items fail to work. When I run ifconfig at this point it only shows my VMNet adapters for VMWare.

2. Once in a while, on a fresh boot, once I get past the login screen it appears that everything freezes. The desktop does not fully load. I have a black background and the top/lower bars but they are blank. My mouse continues to work but there is nothing to click on. The keyboard does not work. I cannot use any key combinations to restart X. I have to perform a hard reset. Obviously this is not a good thing.

I'm not a Linux expert. I've been using it off and on for a few years so I know my way around, but I'm at a loss as to how to troubleshoot these problems. I'll be happy to provide any and all information that I can - just ask me what I need to post and how to get at it. :-)

To start off I'll post the output of LSPCI because I bet that it will be a question....

```

richard@selene:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
richard@selene:~$ 

```

Thank you so much for your assistance in this matter.

Sincerely,
Richard

---

