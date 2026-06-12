---
title: "Vostro 1500 install help"
date: 2008-09-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Chine on 2008-09-16
Hi, this is my first post on the forum and hopefully not my last.  I have been getting errors while trying to install ubuntu on my computer and was hoping you guys could help or send me in the right direction.

I have been following this guide: [http://www.herman.linuxmaniac.net/p24.html](http://www.herman.linuxmaniac.net/p24.html) , but I have been unsuccessful.

Upon clicking "Try Ubuntu without any change to your computer" it begins to load, but I get an error.

[ 155.154901 ] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 155.155058 ] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43devicefirmware](http://linuxwireless.org/en/users/Drivers/b43devicefirmware) and download the correct firmware version (version 4).

After a few seconds, ubuntu loads.  I begin to install ubunto according to that tutorial but while trying to partitian I get an error window that reads:
An error ocurred while writing the changes to the storage devices.  The resize operation has been aborted.

What do these errors mean?  Do I need to download the firmware suggested and I will be able to set the partitian?

Thanks,
Chris

---

### Post by adult swim on 2008-09-16
it might help if you booted your windows install and ran the hard drive defrag.  once you do that then go back and try to modify the partitions.
dont worry about those errors, they are ok for now.

---

### Post by Chine on 2008-09-17
Defraging worked perfectly thanks.  I'm having trouble getting my wireless and video card working.  Any suggestions on that?  I just read that to get the wireless working I should reinstall ubuntu with the network cable plugged in?

---

### Post by adult swim on 2008-09-18
from a terminal, applications>accessories>terminal, type in  ```
lspci
```  (the first letter is a lower case L, not a number 1) and paste the results here.  i doubt that reinstalling with the network cable plugged in would make any difference, so you dont need to reinstall.

---

### Post by Brian Korsedal on 2009-02-26
Hi,

I'm trying to get the same wireless device to work, but on Jaunty 9.04 alpha 4+ (updated).  I was wondering if you could help or if I should just wait?  Here is my lspci

brian@brian-laptop:~$ lspci
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
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
brian@brian-laptop:~$ Ajaunty

---

