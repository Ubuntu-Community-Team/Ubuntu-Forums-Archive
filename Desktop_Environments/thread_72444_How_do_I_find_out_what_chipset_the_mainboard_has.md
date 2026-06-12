---
title: "How do I find out what chipset the mainboard has?"
date: 2005-10-06
forum: Desktop Environments
---

### Post by daller on 2005-10-06
Hi There,

How do I find out what Chipset the motherboard has?

cat /proc/cpuinfo revealed what processor it had!

Is there a KDE-way? (for both situations)

---

### Post by az on 2005-10-06
From a terminal, run
lspci

---

### Post by daller on 2005-10-06
I get this:

0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x] (rev a1)
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
0000:02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
0000:02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
0000:02:03.0 Network controller: Intel Corp. PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

lspci was my first guess, but I can't manage to find it!

---

