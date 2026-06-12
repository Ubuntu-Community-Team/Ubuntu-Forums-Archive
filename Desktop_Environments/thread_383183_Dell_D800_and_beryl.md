---
title: "Dell D800 and beryl"
date: 2007-03-13
forum: Desktop Environments
---

### Post by aknight_sa on 2007-03-13
hello all,

i have a dell D800 laptop which has a Geforce4 420 Go display adapter...
i have installed beryl on it and it kind of worked fine for some time.. then it started to freeze up the whole system after a min or two of startup...

can anyone help

thanks

---

### Post by MikeDX on 2007-03-17
i'm getting a d800 on monday. Currently I run ubuntu 6.10 and beryl fine on a d400, so hopefully the d800 install will be a breeze.

if I get the same problems as you are experiencing, hopefully i'll be able to help out.

---

### Post by MikeDX on 2007-03-21
Hey there

can you give us a little bit more info about your laptop? This is my output from lspci

```

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
02:01.1 CardBus bridge: Texas Instruments PCI7510,7610 PC card Cardbus Controller (rev 01)
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
02:01.3 System peripheral: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

```

I've got just about everything working at the moment except the speed stepping which may be down to the psu being 65W and not 90W so I shall be trying that out in a couple of days once my replacement 90W psu arrives....

---

