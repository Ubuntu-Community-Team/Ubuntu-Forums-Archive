---
title: "Noob Wireless Connection Question"
date: 2009-12-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Biso011 on 2009-12-05
Just installed 9.10 onto my Dell Inspiron b130. Never used Linux before. Installation went smoothly, but I can't seem to get my wireless internet going. Wireless Networks are "disconnected."



  *-network DISABLED
       
description: Wireless interface
       
physical id: 1
       
logical name: wlan0
       
serial: 00:90:4b:e9:aa:15
       
capabilities: ethernet physical wireless
       
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


Can anyone help? Where do I begin? Any assistance is greatly appreciated. Thanks.

---

### Post by mikewhatever on 2009-12-05
Let's start by posting your wireless card info. Open Applications->Accessories->Terminal and post the output of the following command here:
```
sudo lshw -C network
```

---

### Post by ugm6hr on 2009-12-05
The Wifi help? link below has a list of information to provide to get help.

---

### Post by Biso011 on 2009-12-05
Going through the Wifi help? link now. Thanks. Here is the output:


 *-network:0             
       
     description: Ethernet interface
       
     product: BCM4401-B0 100Base-TX
       
     vendor: Broadcom Corporation
       
     physical id: 0
       
     bus info: pci@0000:02:00.0
       
     logical name: eth0
       
     version: 02
       
     serial: 00:14:22:91:d8:6a
       
     size: 10MB/s
       
     capacity: 100MB/s
       
     width: 32 bits
       
     clock: 33MHz
       
     capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

     configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       
     resources: irq:18 memory:dfbfc000-dfbfdfff
  

*-network:1
       
     description: Network controller
       
     product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       
     vendor: Broadcom Corporation
       
     physical id: 3
       
     bus info: pci@0000:02:03.0
       
     version: 02
       
     width: 32 bits
       
     clock: 33MHz
       
     capabilities: bus_master
       
     configuration: driver=b43-pci-bridge latency=64
       
     resources: irq:17 memory:dfbfe000-dfbfffff
  

*-network DISABLED
       
     description: Wireless interface
       
     physical id: 2
       
     logical name: wlan0
       
     serial: 00:90:4b:e9:aa:15
       
     capabilities: ethernet physical wireless
       
     configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by mikewhatever on 2009-12-05
I think the issue may be the same as in the link below.
[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

### Post by Biso011 on 2009-12-05
Ok installed bmcwl-kernel-source and rebooted. Still can't connect to the wireless however. I've attached the updated and requested outputs.

---

### Post by Biso011 on 2009-12-05
Also, I guess it's of secondary importance at the moment, the wired ethernet connection isn't being recognized after the install either. It was working automatically before.. not sure if this is a sign of the wireless problem at all.

---

### Post by mikewhatever on 2009-12-06
Alright, I've done some searching, and it looks like bcmwl-kernel-source
doesn't support you particular model, BCM4318, so please remove it. Most of the howtos mentioning your wireless card suggest installing ndiswrapper, which is a framework to install Windows wireless drivers in Linux. There is also one guide suggesting an open source driver, with your model mentioned vaguely. Hope it works one way or another.
[https://help.ubuntu.com/community/WifiDocs/Driver](https://help.ubuntu.com/community/WifiDocs/Driver)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by coffeeaddict22 on 2009-12-06
Have you checked in System/Administration/Hardware Drivers?  If the Broadcom STA driver is there, I'd strongly suggest you activate it.

---

### Post by drshakaloo on 2009-12-10
I had the exact same problem, (I even have the same model of wireless card and firmware) went through all of the terminal stuff listed here, without any success.  After all that, just for the hell of it, I ran "System Testing" under "Administration", worked through all the various tests, and afterwords, my wireless turned on.  I am currently using it.  I hope it works for you.  Peace.

Micah

---

### Post by Biso011 on 2009-12-12
I'm typing this reply thru the wireless connection! Thanks a ton for the help! I was almost ready to try 9.04 instead. 

It appears ndiswrapper solved the problem. After installing it I was able to activate the broadcom driver for the first time without getting an error. I then unplugged the ethernet cable and restarted. After the reboot I was able to pick up a few wireless signals. I connected to mine and it worked. Restarted a couple times to make sure it was gonna stick and it did. 

Problem solved. Thanks again, a million!

---

