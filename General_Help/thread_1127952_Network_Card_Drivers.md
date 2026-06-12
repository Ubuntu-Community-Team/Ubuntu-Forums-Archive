---
title: "Network Card Drivers"
date: 2009-04-17
forum: General Help
---

### Post by facelesslucifer on 2009-04-17
Hi..........

ubuntu doesn't know network card driver.My network card is wireless and model is "Dell Wireless WLAN 1397 Half MiniCard(4312bg)"

If u know plz give me and how to install it...


Thankz...

---

### Post by facelesslucifer on 2009-04-17
:(:(:(

plz replay urgent for me..

it is important for me

plz 

thankz

---

### Post by roycrom on 2009-04-17
Can you run
```

$ lspci

```
and post the output here?  We can then check what chipset it is using and see where to go from there. I suspect it's using a broadcom chip but lets see.

---

### Post by Daisuke_Aramaki on 2009-04-17
yeah you need to know the wireless card details. what chipset and so on, then we can see if there is support inbuilt in the linux kernel, or if you have to build it yourself. run the command what the previous poster suggested and post the output here.

---

### Post by facelesslucifer on 2009-04-18
this is the output of $lscpi

facelesslucifer@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by roycrom on 2009-04-20
That bottom line is your wireless card - a Broadcom as I suspected.

Take a look at this thread:

[http://ubuntuforums.org/showthread.php?p=6119250#post6119250](http://ubuntuforums.org/showthread.php?p=6119250#post6119250)

and do some searching on "BCM4312 ubuntu 8.10" - there is a lot of info out there.

Things to try are:

Check that the restricted driver is in use - System>Administrator>Hardware Drivers

Install WICD - sudo apt-get install wicd (you may have to search how to do this, try here first [http://www.wicd.net](http://www.wicd.net))

WICD is a different network manager than the stock ubuntu one - it seems to help a lot of people connect when they have had trouble with default network manager.

Hope this helps you get somewhere with your problem.

---

