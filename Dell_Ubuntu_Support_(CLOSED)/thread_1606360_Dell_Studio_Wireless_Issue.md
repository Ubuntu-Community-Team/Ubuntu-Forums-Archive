---
title: "Dell Studio Wireless Issue"
date: 2010-10-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Grey489177 on 2010-10-26
First the stats:
Dell Studio 1737
Ubuntu 10.04 april 2010

Problem:
I installed ubuntu on an dual boot about a week ago and everything was working smooth. Then i took my laptop to work yesterday and when i brought it back the wireless wont enable 
[IMG]http://i55.tinypic.com/24w7hnb.png[/IMG]

What i have already done:
Gone to System>Administration>users and groups>
Set myself with admin privlages, then enabled "Connect to wireless and ethernet networks" along with various other general tricks such as restarting the computer, turning the wireless on and then off, etc.

An odd thing; the wireless wont work but the bluetooth is on and working, but they are both the same device.

Any help would be greatly appreciated.

~Grey

---

### Post by xircon on 2010-10-26
```
sudo gedit /var/lib/NetworkManager/NetworkManager.state
```

If anything says false, change to true, save and reboot.

---

### Post by Grey489177 on 2010-10-26
Didn't work. Here is what i did step by step
Applications>accessories>terminal>sudo gedit /var/lib/NetworkManager/NetworkManager.state

The wireless was set to false, i set it to true>SAVED>rebooted(terminal and gedit still up)

No wireless after reboot, ran sudo again and it said false for wireless again.

Any other ideas?

---

### Post by xircon on 2010-10-26
Try it a couple of times, sometimes it did not work first time.

What is the output of:

```
sudo lshw -C "Network"
```

and 

```
lspci | grep "Network"
```

I am a bit of a one trick pony on wireless, but the above two commands may help somebody else diagnose the problem.

One other thing, if you boot of a live CD can you connect via wireless?

---

### Post by Grey489177 on 2010-10-26
For: 
sudo lshw -C "Network"

 ```
*-network DISABLED      
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fb:91:0c:7c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f8000000-f8001fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:f3:55:8d
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=sb v2.17 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:31 memory:fc500000-fc50ffff
```For: 
lspci | grep "Network"
```
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
```

---

### Post by Grey489177 on 2010-10-26
Just a note, the wireless works when booted up into windows. Just not on the Ubuntu.

---

### Post by bobmartens on 2010-11-01
**Re: Broadcom BCM4312 - Updated Firmware, now no wireless in Windows** 			
 			 			 		   		 		 		I encountered a similar poblemm. After a long search I found something that worked for me, and no harm done if not... 
While starting up, press shift or esc to enter the grub menu. Press e to  edit. To the line that ends with quiet splash, add    pci=noacpi   and  boot, this is not permanent, but my wireless worked flawlessly after  that. I do not remember how to make this permanent, so if this works you  will have to do this every boot.
Did this help?

---

### Post by Grey489177 on 2010-11-01
well, since posting this i have formatted my drive and done away with the dual partition and have ubuntu only installed. After the reinstall the wireless works fine.

---

### Post by xircon on 2010-11-01
Very, very strange!

---

