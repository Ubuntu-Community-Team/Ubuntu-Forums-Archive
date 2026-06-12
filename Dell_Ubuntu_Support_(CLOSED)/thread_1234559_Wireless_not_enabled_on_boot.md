---
title: "Wireless not enabled on boot"
date: 2009-08-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TCSnyder on 2009-08-08
I got my new Dell mini 10 with Ubuntu preinstalled. It has worked great, until now. Every time I shutdown my mini, my wireless doesn't work. I can go to System->Administration->Hardware Drivers and the driver has the box clicked for "Enabled" but it says "Not in use". 

I can disable the driver and then re-enable it and it works, but this is kind of annoying.Any ideas??

Here is my wireless info

```
lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

```
```
lshw
 *-network
                description: Wireless interface
                product: BCM4322 802.11a/b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: 01
                serial: 00:25:56:6b:a4:b8
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl1 driverversion=5.10.79.10 ip=192.168.1.101 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn

```

---

### Post by TCSnyder on 2009-08-08
bump

---

