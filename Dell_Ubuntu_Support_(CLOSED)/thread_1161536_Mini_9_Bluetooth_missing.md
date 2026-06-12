---
title: "Mini 9 Bluetooth missing"
date: 2009-05-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Blue Sassley on 2009-05-16
For some reason in NBR 9.04 the Bluetooth card is missing, but when I was running XP on my Mini the Bluetooth card was there and working.

```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
02:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
02:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

Anyone else seeing any issues on a Mini 9 like this?

Thanks for the help ahead of time
Blue

---

### Post by Blue Sassley on 2009-05-20
I was able to fix the Bluetooth on my Mini 9 by installing aircraft-manager 12.1 from here:

[https://launchpad.net/~opensource-subakutty/+archive/ppa/](https://launchpad.net/~opensource-subakutty/+archive/ppa/)

And re enabled the "software switch" on my Bluetooth.

Blue

---

### Post by tyroeternal on 2009-05-21
I'm sorry I missed your post before!  Bluetooth as well as wireless problems have been reported due to the same program for all of the mini series laptops.  As you said, installing aircraft manager will solve the problem.

---

### Post by Blue Sassley on 2009-05-21
Is there no more adding SOLVED to a thread anymore?

Blue

---

### Post by tyroeternal on 2009-05-21
I think that they removed that feature.  The accepted method, now, is to tag it as solved I suppose.

---

