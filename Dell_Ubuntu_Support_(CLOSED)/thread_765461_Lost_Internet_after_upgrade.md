---
title: "Lost Internet after upgrade"
date: 2008-04-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by donmor on 2008-04-24
Hope someone can help me. I upgraded to 8.04 and lost my wireless and also my 10/100 internet.

Dell 1501  Vista/Ubunto dual boot. Worked with both 7.01 and 7.10 without problems.

This is the results of lshw -C network.

don@don-vista:~$ sudo lshw -C network

  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64

  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:1c:26:30:f0:25
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11

I don't know what to try next to get either the wireless or the wired working.

_NETWORK SETTINGS_
Wireless Connection
Point to Point Connection.

Does not even show a Wired Connection

Thanks for any help

Don

---

### Post by phndrummer on 2009-02-21
My only sugestion is to re-install the driver. Other than that I can't think of anything else. but I'm no expert.

---

### Post by Rallg on 2009-02-22
Try this. It may or may not help, but it is is easy and quick:

Boot to Windows. Get your wireless running there. Then, reboot to Ubuntu. The reboot should be immediate - no shutdown, no power off, no getting up for a snack.

Then, does the wireless work in Ubuntu?

---

