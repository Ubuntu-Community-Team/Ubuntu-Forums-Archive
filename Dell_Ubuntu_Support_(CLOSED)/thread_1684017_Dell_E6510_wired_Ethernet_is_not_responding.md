---
title: "Dell E6510 wired Ethernet is not responding"
date: 2011-02-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pctx on 2011-02-08
Hey guys,

So I'm a Windows guy who is taking the full plunge of going 100% with Ubuntu and using VM's if I need Window stuff.

Recently got a new E6510 for work and got 10.10 32-bit loaded no issues however I cannot get the Ethernet (eth0) to come up and work properly.  Wireless (oddly) works fine.

In my reading of the forums, I've discovered that there's some standard stuff you guys need to determine what's going on so hopefully I get this right.

Here's the outputs:

**cat /etc/network/interfaces**
ahockett@sulaco:~/Desktop$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

**cat /etc/NetworkManager/nm-system-settings.conf**
ahockett@sulaco:~/Desktop$ cat /etc/NetworkManager/nm-system-settings.conf
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

**dmesg | grep -e eth0 -e bcm**
ahockett@sulaco:~/Desktop$ dmesg | grep -e eth0 -e bcm
[    1.330894] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 5c:26:0a:37:19:56
[    1.330896] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.330945] e1000e 0000:00:19.0: eth0: MAC: 9, PHY: 10, PBA No: 2041ff-0ff
[   16.072418] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.964968] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[   19.968025] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   30.071365] eth0: no IPv6 routers present
**ifconfig -a**
ahockett@sulaco:~/Desktop$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr   
          inet6 addr: fe80::5e26:aff:fe37:1956/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1623547 (1.6 MB)  TX bytes:6793 (6.7 KB)
          Interrupt:20 Memory:96900000-96920000 

eth1      Link encap:Ethernet  HWaddr  
          inet addr:10.192.30.15  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::c2cb:38ff:fe34:dbcc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:98663 errors:0 dropped:0 overruns:0 frame:343213
          TX packets:67474 errors:17 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:120680753 (120.6 MB)  TX bytes:7314822 (7.3 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4432 (4.4 KB)  TX bytes:4432 (4.4 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Removed the hardware addresses for security reasons but they are there.

Anyways, I've done some looking around and I've found the e1000e Linux driver from Intel's site, but not sure how to install it.

Thanks a bunch!

-Aaron

---

