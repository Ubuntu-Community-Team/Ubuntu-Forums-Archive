---
title: "Desktop Effects"
date: 2009-03-30
forum: General Help
---

### Post by brandon.r on 2009-03-30
Hello everyone,

I installed ubuntu 8.10 last week, and everythiong was fine. I was able to enable desktop effects.

But after leaving my computer off for a couple of hours, I turned it on and desktop effects was turned off. and now when I try to enable em, it says they  "cannot be enabled"

Any ideas?

Thanks

---

### Post by brandon.r on 2009-03-30
Sorry, I don't usually bump threads. 

but..bump.

---

### Post by damis648 on 2009-03-30
Please, it is forum policy to only bump every 24 to 48 hours. Wait for the people on the other side of the globe to have a chance. :popcorn: Could you give us some details on your graphics card? Post the output of:
```
lspci
```
from the terminal (Applications>Accessories>Terminal).
Also, have you tried rebooting, and have you enabled the restricted drivers for your card? (System>Administration>Hardware Drivers)

---

### Post by brandon.r on 2009-03-30
> **damis648 said:**
> Please, it is forum policy to only bump every 24 to 48 hours. Wait for the people on the other side of the globe to have a chance. :popcorn: Could you give us some details on your graphics card? Post the output of:
```
lspci
```
from the terminal (Applications>Accessories>Terminal).
Also, have you tried rebooting, and have you enabled the restricted drivers for your card? (System>Administration>Hardware Drivers)

I'm sorry. lol im anxious

this is the output:

> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)



And yes, rebooted multiple times. and Theres no restricted driver available to activate.

---

