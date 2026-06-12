---
title: "Wifi not working when ethernet card is enabled"
date: 2005-12-26
forum: General Help
---

### Post by lviggiano on 2005-12-26
I have this problem: on my laptop (dell inspiron 8600) 

I have both eth0 ethernet card adapter [see note 1] and eth1 [see note 2].
They work with ubuntu, but  only if I enable eth0 OR eth1. If I enable both, they obtain an ip address and everything seems fine, but nothing works anymore. In other words, it seems that there is something like a conflict between these two network adapters, that, when they are both enabled, none of them works anymore.
This is out what syslog says when I enable both.

Dec 27 01:17:54 localhost dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 0
Dec 27 01:17:54 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.2
Dec 27 01:17:54 localhost dhclient: Copyright 2004 Internet Systems Consortium.
Dec 27 01:17:54 localhost dhclient: All rights reserved.
Dec 27 01:17:54 localhost dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Dec 27 01:17:54 localhost dhclient:
Dec 27 01:17:54 localhost dhclient: sit0: unknown hardware address type 776
Dec 27 01:17:54 localhost dhclient: sit0: unknown hardware address type 776
Dec 27 01:17:54 localhost dhclient: Listening on LPF/eth1/00:04:23:8f:8b:7e
Dec 27 01:17:54 localhost dhclient: Sending on   LPF/eth1/00:04:23:8f:8b:7e
Dec 27 01:17:54 localhost dhclient: Sending on   Socket/fallback
Dec 27 01:17:57 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Dec 27 01:17:57 localhost dhclient: DHCPOFFER from 192.168.77.1
Dec 27 01:17:57 localhost dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Dec 27 01:17:57 localhost dhclient: DHCPACK from 192.168.77.1
Dec 27 01:17:57 localhost dhclient: bound to 192.168.77.12 -- renewal in 17645 seconds.
Dec 27 01:17:57 localhost dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Dec 27 01:17:57 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.2
Dec 27 01:17:57 localhost dhclient: Copyright 2004 Internet Systems Consortium.
Dec 27 01:17:57 localhost dhclient: All rights reserved.
Dec 27 01:17:57 localhost dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Dec 27 01:17:57 localhost dhclient:
Dec 27 01:17:57 localhost dhclient: sit0: unknown hardware address type 776
Dec 27 01:17:57 localhost dhclient: sit0: unknown hardware address type 776
Dec 27 01:17:57 localhost dhclient: Listening on LPF/eth0/00:0d:56:a9:38:3b
Dec 27 01:17:57 localhost dhclient: Sending on   LPF/eth0/00:0d:56:a9:38:3b
Dec 27 01:17:57 localhost dhclient: Sending on   Socket/fallback
Dec 27 01:18:00 localhost kernel: [4300560.970000] b44: eth0: Link is up at 100 Mbps, full duplex.
Dec 27 01:18:00 localhost kernel: [4300560.970000] b44: eth0: Flow control is on for TX and on for RX.
Dec 27 01:18:01 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 27 01:18:04 localhost kernel: [4300565.433000] eth1: no IPv6 routers present
Dec 27 01:18:07 localhost kernel: [4300568.512000] eth0: no IPv6 routers present
Dec 27 01:18:09 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Dec 27 01:18:10 localhost kernel: [4300570.970000] NETDEV WATCHDOG: eth0: transmit timed out
Dec 27 01:18:10 localhost kernel: [4300570.970000] b44: eth0: transmit timed out, resetting
Dec 27 01:18:10 localhost kernel: [4300570.971000] b44: eth0: Link is down.
Dec 27 01:18:13 localhost kernel: [4300573.971000] b44: eth0: Link is up at 100 Mbps, full duplex.
Dec 27 01:18:13 localhost kernel: [4300573.971000] b44: eth0: Flow control is on for TX and on for RX.
Dec 27 01:18:18 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Dec 27 01:18:18 localhost dhclient: DHCPOFFER from 192.168.77.1
Dec 27 01:18:18 localhost dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Dec 27 01:18:18 localhost dhclient: DHCPACK from 192.168.77.1
Dec 27 01:18:18 localhost dhclient: bound to 192.168.77.3 -- renewal in 18686 seconds.


Notes: 
[1] lspci -v output
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
        Subsystem: Dell: Unknown device 8127
        Flags: bus master, fast devsel, latency 32, IRQ 11
        Memory at faffe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

[2]0000:02:03.0 Network controller: Intel Corp. PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
        Subsystem: Intel Corp.: Unknown device 2561
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at faffc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

Thanks in advance.
Luigi

---

### Post by Lambert on 2005-12-26
1. why would you want two cards enabled at the same time? Do you have a local network and the internet through two different routers and need them both setup? Or another reason

2. Post the output of this command

route

sounds like there's a problem with the routing table and the os doesn't know where to forward the packets to or it's forwarding to the wrong nic which doesn't have a route to the path needed.

---

### Post by lviggiano on 2005-12-27
Hi Lambert!

1. I want them both enabled as I can use them automatically: when the cable is disconnected the wifi will work, and when I am at office (and the wifi is not available) I'll just plug the wire. And... anyway :-), I just like them to work properly.

2. luigi@multivac:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.77.0    *               255.255.255.0   U     0      0        0 eth0
default         192.168.77.1    0.0.0.0         UG    0      0        0 eth0

Thankyou! 
luigi

---

### Post by lviggiano on 2005-12-29
Anyone met same problem ?

---

### Post by kanagawa on 2005-12-30
Yes.

I've got the same problem.

Actually, a very similar problem. Most of the time I get the same message as you, but sometimes I can conncet to the wireless router, if I try to run dhclient wlan0 2 or 3 times. 

Very odd.

---

### Post by 0MG on 2005-12-30
I'm thinking you need to add a default gateway for the wifi.

route add default gw xxx.xxx.xxx.xxx dev wlan0


substitute your wireless router's ip for the x's, and whatever your wireless interface is for wlan0.

Not sure if this will really work as I've never tried it before. I just disable the interface I'm not using when it's not in use. It's a one line command.

---

