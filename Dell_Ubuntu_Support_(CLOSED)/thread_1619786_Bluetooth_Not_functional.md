---
title: "Bluetooth Not functional"
date: 2010-11-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by btencd on 2010-11-12
Dear All,
I am new here and an Ubuntu beginner. I have installed Ubuntu maverick few weeks ago in my new dell 1012 notebook which came with Windows. 
    However, my bluetooth is now not functional though it was working all well when it was running Windows. Any help would be great following are the hardware info:

**tenzin@Digital-Yak:~$ lspci**
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
07:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
tenzin@Digital-Yak:~$ lsussb
No command 'lsussb' found, did you mean:
 Command 'lsusb' from package 'usbutils' (main)
lsussb: command not found
**tenzin@Digital-Yak:~$ lsusb**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 413c:8160 Dell Computer Corp. 
Bus 004 Device 004: ID 413c:8162 Dell Computer Corp. 
Bus 004 Device 003: ID 413c:8161 Dell Computer Corp. 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 15d9:0a4c Trust International B.V. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 003: ID 0c45:641d Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I get error message as no adapters plugged in

any help would be great.

Thankyou

---

### Post by P4man on 2010-11-12
make sure your system is up to date. If it is, also provide the output of 

```
sudo rfkill list
```

If the bluetooth adaptor shows up there, but is listed as "blocked", try running this

```
sudo rfkill unblock all
```

---

