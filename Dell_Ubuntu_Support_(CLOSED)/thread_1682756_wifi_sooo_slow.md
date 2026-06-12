---
title: "wifi sooo slow"
date: 2011-02-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kseel on 2011-02-06
Running Ubuntu 10.10 on a Dell Vostro 1500 laptop. The internet is so slow but it isn't the internet it is fast on everything else. I probably would say it's a driver issue more then anything but I have no idea where to start. 

Thanks,

Kevin

---

### Post by ugm6hr on 2011-02-06
Post the output from:
```
lshw -class network
```

---

### Post by kseel on 2011-02-06
*-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f9ffc000-f9ffffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:c0:23:a6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
       resources: irq:17 memory:f9bfe000-f9bfffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1e:4c:32:c8:d6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A ip=192.168.1.69 multicast=yes wireless=IEEE 802.11bg

---

### Post by ugm6hr on 2011-02-06
You have 2 driver options for the BCM4312 wifi card:
1. b43 (you are using at present)
2. wl
I actually think the latter is better.
To try it out:
[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)
And reboot.

---

### Post by kseel on 2011-02-06
Working like a champ so far thanks.

---

