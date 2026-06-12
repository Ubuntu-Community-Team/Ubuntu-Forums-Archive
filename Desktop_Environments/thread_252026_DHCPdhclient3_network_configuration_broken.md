---
title: "DHCP/dhclient3 network configuration broken"
date: 2006-09-06
forum: Desktop Environments
---

### Post by lycanthrope on 2006-09-06
System is configured for DHCP & has been working for ~2 months.  Starting yesterday (first noticed), the networking configuration is failing - requests IP, gets IP from DHCP server, says it's binding to IP, but actually binds to a 169.xxx.xxx.xxx addr... Looking for solution or pointers to fix this.

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                           Version                        Description
+++-==============================-==============================-============================================================================
ii  dhcp3-client                   3.0.3-6ubuntu7                 DHCP Client

rthompso@jhereg:~$ dpkg -l dhcp3-common
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                           Version                        Description
+++-==============================-==============================-============================================================================
ii  dhcp3-common                   3.0.3-6ubuntu7                 Common files used by all the dhcp3* packages




rthompso@jhereg:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                                                                                           Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:07:e9:e0:fa:7f
Sending on   LPF/eth0/00:07:e9:e0:fa:7f
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.100.226 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:07:e9:e0:fa:7f
Sending on   LPF/eth0/00:07:e9:e0:fa:7f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.100.226
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.100.226
bound to 192.168.100.8 -- renewal in 5550 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

This looks right, and should be fine, however, /sbin/ifconfig shows that eth0 is bound to a 169.x.x.x addr (inet addr:169.254.199.247 ).  So we're asking for an IP, we're getting an IP, but we're setting eth0 to a 169 addr even though we say we're bound to a correct IP.  Additionally, the script attempts to set eth1, eth2, ath0, and wlan0 -- none of which are existant on my machine.  Screen paste and system info listed below.

rthompso@jhereg:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:E9:E0:FA:7F  
          inet addr:169.254.199.247  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::207:e9ff:fee0:fa7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16925 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20872923 (19.9 MiB)  TX bytes:3909137 (3.7 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:61377 (59.9 KiB)  TX bytes:61377 (59.9 KiB)

rthompso@jhereg:~$ 
rthompso@jhereg:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                                                                                           Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:07:e9:e0:fa:7f
Sending on   LPF/eth0/00:07:e9:e0:fa:7f
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.100.226 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:07:e9:e0:fa:7f
Sending on   LPF/eth0/00:07:e9:e0:fa:7f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.100.226
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.100.226
bound to 192.168.100.8 -- renewal in 5550 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                                                                                          [ ok ]
rthompso@jhereg:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:E9:E0:FA:7F  
          inet addr:169.254.107.229  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::207:e9ff:fee0:fa7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29998 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17317 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21108406 (20.1 MiB)  TX bytes:3994437 (3.8 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:229 errors:0 dropped:0 overruns:0 frame:0
          TX packets:229 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63133 (61.6 KiB)  TX bytes:63133 (61.6 KiB)

rthompso@jhereg:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:E9:E0:FA:7F  
          inet addr:169.254.107.229  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::207:e9ff:fee0:fa7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30997 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17897 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21379233 (20.3 MiB)  TX bytes:4226193 (4.0 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:229 errors:0 dropped:0 overruns:0 frame:0
          TX packets:229 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63133 (61.6 KiB)  TX bytes:63133 (61.6 KiB)

rthompso@jhereg:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                           Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:07:e9:e0:fa:7f
Sending on   LPF/eth0/00:07:e9:e0:fa:7f
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.100.226 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:07:e9:e0:fa:7f
Sending on   LPF/eth0/00:07:e9:e0:fa:7f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.100.226
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.100.226
bound to 192.168.100.8 -- renewal in 5749 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                                                                                          [ ok ]
rthompso@jhereg:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:E9:E0:FA:7F  
          inet addr:169.254.114.230  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::207:e9ff:fee0:fa7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18049 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21397698 (20.4 MiB)  TX bytes:4240178 (4.0 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:229 errors:0 dropped:0 overruns:0 frame:0
          TX packets:229 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63133 (61.6 KiB)  TX bytes:63133 (61.6 KiB)

---

### Post by lycanthrope on 2006-09-06
Resolved:  system was loading e100 network module, should have been loading eepro100 module.  Added e100 to 

root@jhereg:/etc/modprobe.d# cat blacklist-e100
blacklist e100

Added eepro100 to 

root@jhereg:/etc# cat modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
eepro100

---

