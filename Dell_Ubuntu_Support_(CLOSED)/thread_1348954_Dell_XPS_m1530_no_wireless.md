---
title: "Dell XPS m1530 no wireless"
date: 2009-12-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by genjix on 2009-12-07
Hey,

My sister got a brand new laptop today. She's installed Ubuntu on it. Wireless isn't working.

I found this thread. [https://bugs.launchpad.net/dell/+bug/190664](https://bugs.launchpad.net/dell/+bug/190664)

I've installed the restricted Broadcom chipset and also tried ndiswrapper but when I run,

```
# dhclient eth2
```

It just keeps trying and never connects.

She uses it for work so we're looking for suggestions. She accidentally installed the 32bit ver but not sure it matters much (will try 64bit tomorrow).

---

### Post by genjix on 2009-12-07
```
root@the-accountant:~# iwconfig wlan2 essid theinternets
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan2 ; No such device.
root@the-accountant:~# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11abgn  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:14 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          
root@the-accountant:~# dhclient eth2
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth2/00:26:5e:1a:ef:af
Sending on   LPF/eth2/00:26:5e:1a:ef:af
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@the-accountant:~# 
```
With my open network using the Ubuntu proprietary broadcom driver.

---

### Post by coffeeaddict22 on 2009-12-08
Hi Genjix,
need more info.  It looks like you've got a working card- it seems to be able to scan at least.  Could you post the output of ```
lshw -C network 
nm-tool
```
iwconfig gives you more info if run with sudo in foront of it too; particularly, it'll tell you the name of the network the card can see.

---

