---
title: "ndiswrapper and kubuntu beta :/"
date: 2006-04-21
forum: Desktop Environments
---

### Post by katana2k on 2006-04-21
I just did a fresh install of kubuntu beta and my wireless card still wasnt supported. no big deal, i would just have to use ndiswrapper. I followed the instructions from the ndsiwrapper setup howto on the ubuntu wiki and everything worked fine... until i tried to get on the iternet. 

i can see my card (wlan0) in the ifconfig and iwconfig, i can see wireless networks, but when i connect to them i cant get on the internet or even ping a website.

when i do ifdown wlan0 then ifup wlan0, i get the following:

```
**root@ubuntu:/etc/network# ifdown wlan0**
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:0c:41:b4:8e:c8
Sending on   LPF/wlan0/00:0c:41:b4:8e:c8
Sending on   Socket/fallback
wlanctl-ng: Operation not supported
**root@ubuntu:/etc/network# ifup wlan0**
wlanctl-ng: Operation not supported
Failed to enable the device, exitcode= 1 .
run-parts: /etc/network/if-pre-up.d/linux-wlan-ng-pre-up exited with return code 1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:0c:41:b4:8e:c8
Sending on   LPF/wlan0/00:0c:41:b4:8e:c8
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Error : Name or service not known
root@ubuntu:/etc/network#           
```

this is what my /etc/network/interfaces looks like:

```
  GNU nano 1.3.10                        File: interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface

auto eth0
iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid auntymauva

auto wlan0


```

any ideas?

**edit:**
im using a Linksys WPC11 ver. 4 with driver NET8180.inf 
my network card has a realtek chipset im pretty sure

---

