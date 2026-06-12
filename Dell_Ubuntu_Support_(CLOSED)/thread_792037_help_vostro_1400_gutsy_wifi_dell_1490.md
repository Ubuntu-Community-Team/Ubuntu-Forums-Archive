---
title: "help vostro 1400 gutsy wifi dell 1490"
date: 2008-05-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by arhk on 2008-05-12
hi this is my first post, I just installed ubuntu on the weekend and have been trying to get the wifi working. I've installed ndiswrapper using this tutorials, but it still doesn't work.

[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

here are diferent outputs:

output of 'ndiswrapper -l'
bcmwl6 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)

output of 'ndiswrapper -v'
utils version: 1.9
driver filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 586 

output for 'sudo lshw -C network'
 *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:fa:d5:ae
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full ip=10.25.157.194 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

plz help me, this is my first time in linux. If you need more info plz ask. Thanks

---

### Post by arhk on 2008-05-12
anyone? :(

---

### Post by slowlap on 2009-04-27
Why don't you just try using intrepid instead or jaunty, my Dell Vostro 1400 wifi seems to work fine, but i did have to do a tiny bit of terminal work for intrepid to get the lights to work properly.Google wifi lights and usually you'll find a bit of terminal giggery pokery to sort you out

---

### Post by dark_religion on 2009-11-13
I tried using intrepid instead or jaunty and it worked for me.

---

