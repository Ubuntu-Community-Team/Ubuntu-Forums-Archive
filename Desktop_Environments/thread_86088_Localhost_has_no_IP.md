---
title: "Localhost has no IP"
date: 2005-11-04
forum: Desktop Environments
---

### Post by Eproxus on 2005-11-04
My localhost seems to have no IP. This screws up CUPS among other things and * Stopping the Domain Name Service at shutdown freezes my computer. Somehow localhost gets no IP at boot, how can I fix this?

Output from ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr ??:??:??:??:??:??
          inet addr:129.16.46.178  Bcast:129.16.47.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:142272 errors:1938654 dropped:0 overruns:0 frame:1938654
          TX packets:23606 errors:0 dropped:0 overruns:0 carrier:0
          collisions:8803 txqueuelen:1000
          RX bytes:43493904 (41.4 MiB)  TX bytes:2863365 (2.7 MiB)
          Interrupt:11 Base address:0x8000

eth1      Link encap:Ethernet  HWaddr ??:??:??:??:??:??
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth3      Link encap:UNSPEC  HWaddr ??-??-??-??-??-??-00-00-00-00-00-00-00-00-00-00
          BROADCAST MULTICAST  MTU:2312  Metric:1
          RX packets:142272 errors:1938654 dropped:0 overruns:0 frame:1938654
          TX packets:23606 errors:0 dropped:0 overruns:0 carrier:0
          collisions:8803 txqueuelen:100
          RX bytes:43493904 (41.4 MiB)  TX bytes:2863365 (2.7 MiB)
          Interrupt:11 Base address:0x8000

lo        Link encap:Local Loopback
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

``` 
My /etc/hosts file:
```
127.0.0.1 localhost.localdomain localhost kaze

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

``` 
I'm running the latest Kubuntu (5.10).

---

### Post by Harleen on 2005-11-04
I suspect an error in your /etc/network/interfaces, so the interfaces aren't configured correctly during startup.

A quick fix is to manually configure that device with "sudo ifconfig lo inet 127.0.0.1".

---

