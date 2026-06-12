---
title: "Dell Dimension 2300 Marvell 88w8335 Wireless help"
date: 2010-07-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Revolutionary101 on 2010-07-24
I recently installed Ubuntu on my friend's Dell Dimension 2300 computer and it runs great, except for one thing, the wireless does not work. This is a major thing because his desktop is not close to an Ethernet port. I know that I need ndiswrapper and I have already installed the GUI version of it. This is the result of the lspci command:
```
user@user-desktop:~$ lspci
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
01:04.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

```
I have been looking for the Windows .inf driver file to install but I can't find it for the 88w8335 wireless card. I have looked around on the internet for it, but I have not been able to find it. Some sites have said that it uses a Trendnet chipset and others have said that it is a Belkin.

Any help would be greatly appreciated.

---

### Post by Revolutionary101 on 2010-07-25
Does anyone have an answer to my predicament?

---

### Post by Revolutionary101 on 2010-07-26
I solved this by following this tutorial:

[https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k)

---

