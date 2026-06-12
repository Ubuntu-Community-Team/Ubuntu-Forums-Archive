---
title: "Dell 1450 wireless issue in Ubuntu 10.04 (Linux 2.6.32.22-generic)"
date: 2010-05-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by totziens on 2010-05-09
I am using Dell Studio 1450. I have been struggling with one problem with another since Ubuntu 10.04 has been installed - mostly wireless and sound issues. When I thought I have fixed the wireless issue, I encountered the same problem when I upgraded to Linux 2.6.32.22-generic.

The Hardware Driver activation method worked for me initially when  Ubuntu 10.04 (Linux 2.6.32.21-generic) was installed. However, when it&#8217;s  upgraded to Linux 2.6.32.22-generic, the same problem happened again.  Deactivate the driver and re-activate do not help. &#8220;sudo apt-get install  bcmwl-modaliases&#8221; does not help at all because the version I am  having is already the latest one.

Here are some info that I am not sure whether it's helpful:

totziens@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 12)
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 12)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] [1002:68e0]
01:00.1 Audio device [0403]: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] [1002:aa68]
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
05:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4353] (rev 01)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
totziens@ubuntu:~$ lsusb
Bus 002 Device 007: ID 413c:8160 Dell Computer Corp. 
Bus 002 Device 006: ID 413c:8162 Dell Computer Corp. 
Bus 002 Device 005: ID 413c:8161 Dell Computer Corp. 
Bus 002 Device 004: ID 046d:c05d Logitech, Inc. 
Bus 002 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6407 Microdia 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
totziens@ubuntu:~$ dmesg | grep -e wlan
totziens@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:24:e8:83:a7:ba
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=sb ip=192.168.0.100 latency=0 multicast=yes
       resources: irq:35 memory:f0300000-f030ffff
  *-network DISABLED
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: f0:7b:cb:5d:ff:4f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:f0400000-f0403fff

totziens@ubuntu:~$ uname -rm
2.6.32-22-generic x86_64

totziens@ubuntu:~$ sudo iwlist scan
[sudo] password for totziens: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

---

