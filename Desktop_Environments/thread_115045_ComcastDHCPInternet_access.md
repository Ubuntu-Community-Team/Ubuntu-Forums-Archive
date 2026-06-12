---
title: "Comcast/DHCP/Internet access"
date: 2006-01-09
forum: Desktop Environments
---

### Post by LanceM on 2006-01-09
I am having what appears to be problems with DHCP and my cable modem from Comcast. I am trying to replace my Fedora box with a new Ubuntu box. I took the new box to work and successfully installed Ubuntu 5.10. When I brought the box home and plugged in my cable modem, I am not getting assigned an ip. Here is what I have:

**ifconfig eth0**
eth0      Link encap:Ethernet  HWaddr 00:13:20:E5:D4:95
          inet6 addr: fe80::213:20ff:fee5:d495/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1253 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:80514 (78.6 KiB)  TX bytes:2430 (2.3 KiB)

**/etc/network/interfaces**

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

auto eth0

**ifup/ifdown:**

home:/sbin$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 7238
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:13:20:e5:d4:95
Sending on   LPF/eth0/00:13:20:e5:d4:95
Sending on   Socket/fallback

home:/sbin$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:13:20:e5:d4:95
Sending on   LPF/eth0/00:13:20:e5:d4:95
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Any help would be great, I am out of ideas.

Thanks,
Lance

---

### Post by LanceM on 2006-01-09
Much ado about nothing...I figured it out.

The cable modem was bound to my old MAC address. It's better now.

---

