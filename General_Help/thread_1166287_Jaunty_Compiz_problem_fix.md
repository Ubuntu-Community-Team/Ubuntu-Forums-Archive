---
title: "Jaunty Compiz problem fix"
date: 2009-05-21
forum: General Help
---

### Post by DariusS on 2009-05-21
After recently doing a clean upgrade to 9.04, I noticed (both x86 and 64 versions) that compiz wouldn't work. I kept getting errors about compiz being unable to start, and after some digging and searching, found out that my graphics card was blacklisted. In previous versions of Ubuntu, compiz had always worked great, so I didn't think it would be too harmful bypassing the blacklist (not recommended though).

here's some quick info about my system for context:
Acer Aspire 5920 laptop, running intel core 2 duo (dual 2.0Ghz)

output of lspci:
```
adam@adam-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

I had followed several tutorials about intel graphics in Jaunty, but it wasn't until I found [[COLOR="Red"]Forlong's post about Compiz-Check[/COLOR]]("http://ubuntuforums.org/showthread.php?t=799070") that I found the problem and was able to work around it. This hand script not only checks if you can run Compiz, but if you can't, it'll tell you why. Also, in my case of having a blacklisted card (or maybe just chipset...) it asked if I wanted to bypass the blacklist, and automagically Compiz was up and running after!

So, here's a link to the site where you can download Compiz-Check, but remember, all credit goes to Forlong!!
[URL="http://forlong.blogage.de/entries/pages/Compiz-Check"]
[COLOR="Red"]http://forlong.blogage.de/entries/pages/Compiz-Check[/COLOR][/URL]

---

### Post by rohitfeb14 on 2009-05-26
Bypassing will cause your system to crash..
So do not do that..
Work on new driver is under progress and u will be able to do everything soon

---

