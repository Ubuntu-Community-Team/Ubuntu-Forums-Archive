---
title: "Enable Wireless on Dell Inspiron E1405"
date: 2008-12-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hucknbid on 2008-12-09
I am brand new to using linux, so fogive my massive amounts of ignorance.
I just put Ubuntu 8.10 on my Dell Inspiron E1405 last night. The wireless was not working so I followed the directions in the help file to use a windows driver using ndisgtk. After trying every .inf file in every driver I was able to find on Dell's driver website (R151519, R115320, and R129083) none of them worked. I then noticed that there were 300 some updates to be downloaded so I left those to download overnight, hoping that one might be the correct driver. After the update I restarted and there was a "Broadcom B43 wireless driver" listed under Hardware Drivers, which I enabled and is currently running, but still no luck. I ran "sudo lshw -C network" on the terminal and got this back:

luke@luke-laptop:~$ sudo lshw -C network
[sudo] password for luke: 
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:77:3f:56
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=160.94.153.81 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ba:7d:fb:09:ef:3c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
 
It would appear that the wireless card is disabled, and I have no idea how to enable it. I even disabled and re-enabled the wireless card from the BIOS to see if that would solve it, no luck. I am considering starting over with an older version of Ubuntu to see if the issue might just be in 8.10, but I'd prefer not to have to downgrade. Any suggestions or directions to other places to look for help would be greatly appreciated.

---

### Post by creolbuay on 2009-04-30
I think you need to upgrade to 9.04 if you haven't yet. I have it running on my E6400 and have not had any issues with it. I even got the internal Sprint card to work.

---

