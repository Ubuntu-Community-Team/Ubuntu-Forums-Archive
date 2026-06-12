---
title: "Routing table"
date: 2006-09-03
forum: Desktop Environments
---

### Post by wugoat on 2006-09-03
Hi Ubuntu Land!

Trying to set up a webproxy for the home lan. Ubuntu box has 2 NIC's... Configured simularly to the Firestarter Help suggests (Very helpful reference!). Eth0(static IP) internal facing the LAN, and eth1(DHCP) external facing the router.

  But I can't ping Lan IP's.  I used Network Tools traceroute to see the pings route, and noticed it hops from my external facing interface(eth1).

  OK, here's where we start skimming the edges of my knowledge. :D I think this means the problem is with my routing table:

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
```

Am I right in thinking this sets all traffic for the LAN (192.168.1.x)through both eth1 and eth0?  I guess it hits eth1 first, and sends it out to the router. What I want is that traffic to go through eth0 to the LAN.

If so what is the remedy?

for completeness:
```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:21:D3:C6:E7
          inet addr:192.168.1.37  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:21ff:fed3:c6e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:936 (936.0 b)
          Interrupt:12 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:20:18:2B:E6:8F
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::220:18ff:fe2b:e68f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4923 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2687 errors:0 dropped:0 overruns:0 carrier:0
          collisions:14 txqueuelen:1000
          RX bytes:2342075 (2.2 MiB)  TX bytes:407514 (397.9 KiB)
          Interrupt:9 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:90 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5956 (5.8 KiB)  TX bytes:5956 (5.8 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by wugoat on 2006-09-05
O:)

Just to close the circle...

I was right... and the fix is to set the 2 network cards to point to different subnets.
  So I changed the IP of my Internal facing NIC, and all LAN Nic's to [SIZE="4"]192.168.[COLOR="Red"]2[/COLOR].xxx[/SIZE]  and I can now ping through to google from the LAN(and traceroute confirms that it's all behaving itself!).  
Of course I could have changed my router/external facing NIC to the different subnet... But LAN's easier as my router doesn't want to show its' interface when I'm on Ubuntu(pro'lly cos it's eth not usb, and I've tweaked a setting somewhere :evil: ).

Right!  Now I'm off to battle the wicked Squid(don't forget to change those ACL's to the new LAN address range!) & Dansguardian...

---

