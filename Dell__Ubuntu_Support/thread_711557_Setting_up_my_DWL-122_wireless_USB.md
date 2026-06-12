---
title: "Setting up my DWL-122 wireless USB"
date: 2008-02-29
forum: Dell  Ubuntu Support
---

### Post by whitematter33 on 2008-02-29
Yeah so I did this one time before, but since I reformatted and re-installed my ubuntu, I am having this trouble again. I can't seem to remember what I did last time, not only that, I think my last install was done with a combination of ndiswrapper and linux-wlan-ng. 

Here is what I know so far. 
iwconfig returns:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.


And my sudo lshw says:

 *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: wlan0
       serial: 00:0d:88:66:52:a2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_usb driverversion=0.2.8 link=no multicast=yes

I think linux-wlan-ng is preinstalled on 7.10, and I have checked the supported wireless list to make sure that this USB is supported, but I don't know why I am unable to connect. Because I think my computer recognizes the driver, but fails to recognize it as a wireless. 

Any help is appreciated, and I am using a Inspiron 2200 in case that changes something.

---

