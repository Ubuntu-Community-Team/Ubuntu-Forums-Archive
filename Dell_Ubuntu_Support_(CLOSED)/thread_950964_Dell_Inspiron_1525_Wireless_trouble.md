---
title: "Dell Inspiron 1525 Wireless trouble"
date: 2008-10-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by da61 on 2008-10-17
Hello, I have a Dell Inspiron 1525 computer and i recently installed ubuntu 8.04 and my wireless is not working, ive trying to find on the web how to fix this but i've been trough 5 pages on google in every keywords i try but nothing works, i actually learned a littlebit on the terminal so i should be able to understand some instruction. (im a first time linux user) any ways here are some info i get when i type lspci and lshw -C network in the terminal ( im not ever sure i see any wireless cards, but i dont quite understand this) im pretty sure i have a 1505 mini w-card, it worked perfectly with windows xp. 

thanks

```
Lspci


dx@dx-laptop:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)

02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)

02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)

02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)

02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)

0b:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

dx@dx-laptop:~$ 
```

```
lshw -C network


dx@dx-laptop:~$ lshw -C network

WARNING: you should run this program as super-user.

*-network

description: Ethernet interface

product: 88E8040 PCI-E Fast Ethernet Controller

vendor: Marvell Technology Group Ltd.

physical id: 0

bus info: pci@0000:09:00.0

logical name: eth0

version: 12

serial: 00:1d:09:5f:19:35

width: 64 bits

clock: 33MHz

capabilities: bus_master cap_list ethernet physical

configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes

*-network UNCLAIMED

description: Network controller

product: BCM4310 USB Controller

vendor: Broadcom Corporation

physical id: 0

bus info: pci@0000:0b:00.0

version: 01

width: 64 bits

clock: 33MHz

capabilities: bus_master cap_list

configuration: latency=0

dx@dx-laptop:~$ 
```

---

