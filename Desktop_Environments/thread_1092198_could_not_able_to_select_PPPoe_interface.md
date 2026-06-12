---
title: "could not able to select PPPoe interface"
date: 2009-03-10
forum: Desktop Environments
---

### Post by rajasekhar_chary on 2009-03-10
Hi All,

I am a new bee to ubuntu, recently I have installed ubuntu in my HP lappy through wubi.

I could not able to connect wired internet,infact I could not able to select the PPOe network interface through checkbox. below is the sys log for above operation

Mar 9 23:06:46 purnima-laptop kernel: [ 103.284945] NET: Registered protocol family 24
Mar 9 23:06:48 purnima-laptop kernel: [ 104.097085] sky2 eth0: disabling interface
Mar 9 23:06:48 purnima-laptop kernel: [ 104.188787] sky2 eth0: enabling interface
Mar 9 23:06:48 purnima-laptop kernel: [ 104.194778] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 9 23:06:50 purnima-laptop kernel: [ 104.600718] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Mar 9 23:06:50 purnima-laptop kernel: [ 104.604199] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Mar 9 23:07:00 purnima-laptop kernel: [ 106.146077] eth0: no IPv6 routers present


few more info

purnima@purnima-laptop:~$ sudo dhclient eth0
[sudo] password for purnima:
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1d:72:54:b5:b6
Sending on LPF/eth0/00:1d:72:54:b5:b6
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


================================================== ======


purnima@purnima-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
purnima@purnima-laptop:~$

Please help me in solving this problem. Also let me know if anyone need more information

Thanks,
Rajasekhar

---

