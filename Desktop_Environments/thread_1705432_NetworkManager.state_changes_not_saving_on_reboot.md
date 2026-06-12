---
title: "NetworkManager.state changes not saving on reboot"
date: 2011-03-12
forum: Desktop Environments
---

### Post by ScriptMaverick on 2011-03-12
This is my last attempt at solving this issue before I have to return to windows as I need to contact family via web.
I am unable to connect to the wireless network at home since upgrading to Ubuntu 10 desktop. It worked fine on v9.
I reinstalled a full U 10 version but same issue.
I am trying to enable wireless in the file mentioned as this seems to solve most posters issues but for some reason when I reboot it loses the update.
I've tired logged in as su and sudo i but no joy.
Any help would be appreciated.

---

### Post by garvinrick4 on 2011-03-12
Tell users what type of wifi card you are using!
```
sudo lshw -C network > network.txt 
```
Will put a text file in home copy and paste here.

---

### Post by ScriptMaverick on 2011-03-12
sorry guys...
here's the output.... thanks for your time
 
*-network:0 DISABLED
description: Wireless interface
product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
vendor: Intel Corporation
physical id: 4
bus info: pci@0000:02:04.0
logical name: eth1
version: 04
serial: 00:0c:f1:2f:35:c1
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=64 link=no maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
resources: irq:11 memory:90080000-90080fff
*-network:1
description: Ethernet interface
product: NetXtreme BCM5705M_2 Gigabit Ethernet
vendor: Broadcom Corporation
physical id: e
bus info: pci@0000:02:0e.0
logical name: eth0
version: 03
serial: 00:08:02:e4:e4:56
capacity: 1GB/s
width: 64 bits
clock: 66MHz
capabilities: pm vpd msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 firmware=5705-v3.14 latency=64 link=no mingnt=64 multicast=yes port=twisted pair
resources: irq:11 memory:90000000-9000ffff memory:5c000000-5c00ffff
*-network DISABLED
description: Wireless interface
product: Belkin
vendor: Belkin
physical id: 3
bus info: pci@0000:05:00.0
logical name: wlan0
version: 20
serial: 00:17:3f:d5:b0:b1
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rtl8180 driverversion=2.6.35-22-generic firmware=N/A latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
resources: irq:10 ioport:4800(size=256) memory:64000000-640003ff

---

### Post by ScriptMaverick on 2011-03-12
BELKIN Wireless G Notebook MODEL F5D7010...

---

### Post by garvinrick4 on 2011-03-12
I will give you a bump someone should understand why you are Disabled on
your wireless.

---

### Post by ScriptMaverick on 2011-03-13
Any help guys? This is my last day running LINUX at home if not. Really won't want to go back to Wins after experiencing joys of U v9.
Disappointed with ve 10.

---

