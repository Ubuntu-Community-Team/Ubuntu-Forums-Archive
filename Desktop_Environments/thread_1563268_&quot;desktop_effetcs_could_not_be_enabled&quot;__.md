---
title: "&quot;desktop effetcs could not be enabled&quot;  10.04"
date: 2010-08-28
forum: Desktop Environments
---

### Post by Shelbsterina on 2010-08-28
My computer and I have been without internet for quite sometime now, until yesterday. The first thing I did was upgrade from 8.04, to 10.04. Hardy has been the only version that ever really worked right with everything, but I figured I'd give Lucid a try since it's LTS, too.

Well, I've been trying to get my desktop looking all nifty again, but I can't enable desktop effects. I've Googled for solutions and can't seem to find one that works for me.

Here's the output from "lspci", if it's relevant:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:05.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)


Is there some driver I'm missing and need to get? Thanks in advance.

---

### Post by clhsharky on 2010-08-29
Shelbsterina

Intel riped out old UMS drivers for new KMS drivers.
There are some workarounds, but nothing like the old drivers that were good in Linux.
This may help with what Intel is now doing to resolve there(mess up) with vintage drivers.
[http://www.phoronix.com/scan.php?page=news_item&px=ODU0Ng](http://www.phoronix.com/scan.php?page=news_item&px=ODU0Ng)
and
[http://www.phoronix.com/scan.php?page=news_item&px=ODU0OA](http://www.phoronix.com/scan.php?page=news_item&px=ODU0OA)


Sharky

---

