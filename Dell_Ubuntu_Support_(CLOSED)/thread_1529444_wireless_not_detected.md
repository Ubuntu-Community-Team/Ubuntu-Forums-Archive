---
title: "wireless not detected"
date: 2010-07-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by paulXPS on 2010-07-12
Installed Ubuntu on my laptop. Everything working great except for the wireless card. Any ideas on what Could be the problem?. I have a dell inspiron 1720 my dell service tag is 5v29f1

---

### Post by realzippy on 2010-07-12
...first we need to know which network card you use.Might be a
Broadcom Corporation.Open a terminal,type:

```
lspci
```

and post the output.

According to

[http://support.dell.com/support/topics/global.aspx/support/my_systems_info/en/details?c=us&l=en&s=hied](http://support.dell.com/support/topics/global.aspx/support/my_systems_info/en/details?c=us&l=en&s=hied)

your posted dell service TAG is invalid...

---

### Post by paulXPS on 2010-07-12
service tag is  5V29SF1

---

### Post by realzippy on 2010-07-12
It says wireless is 4312BG....no rev nr.

Can you open a terminal and post the output?Type in terminal:

```
lspci
```


If you do not know how to open a terminal,press Alt+F2 and type: gnome-terminal

---

### Post by realzippy on 2010-07-12
**If** it is a broadcom 4312,try this:

Make sure that "restricted" repository is enabled:
Go to system>administration>software sources and enable
proprietary drivers for devices (restricted).Then open a 
terminal,type:

```
sudo apt-get update
```

```
sudo apt-get install bcmwl-kernel-source
```

Then go to

System > Administration > Hardware Drivers

and see if a driver is offered now(broadcom),if so,enable it
(may take a short while),then reboot.

---

### Post by paulXPS on 2010-07-12
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by jarviser on 2010-07-12
> **paulXPS said:**
> 
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Broadcom again! Must be the most common complaint on here for wifi.

Isn't it about time someone posted a Sticky with the Broadcom wifi fixes?

---

### Post by realzippy on 2010-07-13
0c:00.0 Network controller: Broadcom Corporation [COLOR="Lime"]BCM4312[/COLOR] 802.11b/g (rev 01)


...so do what suggested in post #5

---

### Post by Megaptera on 2010-07-13
I've had success with this simple fix on various -buntu derivatives of 9.10 and 10.04 on my Dell Inspiron:

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

... don't forget to reboot though.

Hope this helps?

---

### Post by s9032g@comcast.net on 2010-07-14
install WICD it will solve your problem. Network Mgr does not work.

---

### Post by jarviser on 2010-07-14
> **s9032g@comcast.net said:**
> .....Network Mgr does not work.

Works fine for me, on Wifi and 3G  It may be problemmatic on some machines of course.

---

