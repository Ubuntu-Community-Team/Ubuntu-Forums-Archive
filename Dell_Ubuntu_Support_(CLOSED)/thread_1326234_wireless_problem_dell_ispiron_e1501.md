---
title: "wireless problem dell ispiron e1501"
date: 2009-11-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by maganga on 2009-11-14
iam begineer of ubuntu i have problem ma laptop cant detect wireless when i type 
in terminal   sudo  lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth3
       version: 02
       serial: 00:1c:23:a6:a5:97
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=196.44.166.219 latency=64 module=ssb multicast=yes
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan2
       serial: 00:1a:73:46:43:1b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: d6:fc:44:82:9b:64
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
maganga@maganga:~$

---

### Post by mikewhatever on 2009-11-14
If you have the latest version of Ubuntu installed, you might be affected by the bug discussed in this thread:
[http://ubuntuforums.org/showthread.php?t=1323746](http://ubuntuforums.org/showthread.php?t=1323746)

---

