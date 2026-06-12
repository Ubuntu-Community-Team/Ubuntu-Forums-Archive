---
title: "Network connection problems- bizarre (need to reboot router for anything to work)"
date: 2005-11-30
forum: Desktop Environments
---

### Post by paulchuck on 2005-11-30
I am working with a fresh install of latest prod ubuntu release (5.1) on an HP Laptop.    The network card is listed as  Accton EN2242 Series MiniPCI Fast Ethernet Adapter.  After booting the machine, I have an IP (according to the little network icon in gnome) but I am not able to access any network resources (can't ping gateway).  Ifdown ifup does not help.  Unplugging net cable, pluggling back in does not help.  The only way I can get a network connection is to unplug power from router, and then plug back in.  After that everything works fine.  The router is an SMC 7004WBR, but works fine with every other machine that is connected (including this one before installing Ubuntu).  Anyways, roomates are getting pissed that I keep rebooting router, so any help would be appreciated.  Let me know if you need any more info, and thanks for you help!:confused:

---

### Post by N6546R on 2005-11-30
What's the output of the commands "route -n" and "ifconfig" before you reboot the router, and after?

Perry

[QUOTE=paulchuck]I am working with a fresh install of latest prod ubuntu release (5.1) on an HP Laptop.    The network card is listed as  Accton EN2242 Series MiniPCI Fast Ethernet Adapter.  After booting the machine, I have an IP (according to the little network icon in gnome) but I am not able to access any network resources (can't ping gateway).  Ifdown ifup does not help.  Unplugging net cable, pluggling back in does not help.  The only way I can get a network connection is to unplug power from router, and then plug back in.  After that everything works fine.  The router is an SMC 7004WBR, but works fine with every other machine that is connected (including this one before installing Ubuntu).  Anyways, roomates are getting pissed that I keep rebooting router, so any help would be appreciated.  Let me know if you need any more info, and thanks for you help!:confused:[/QUOTE]

---

### Post by paulchuck on 2005-12-02
Perry-

Thanks for the response.  Here is the info you requested.  Let me know if you need anything else.
I also did an ifdown/up so you can see the output from that.

_______BEFORE________
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
paul@lilcomp:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:D0:59:7A:B5:B6
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fe7a:b5b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7832 (7.6 KiB)  TX bytes:5203 (5.0 KiB)
          Interrupt:11 Base address:0x8c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:257 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:21526 (21.0 KiB)  TX bytes:21526 (21.0 KiB)
paul@lilcomp:~$ sudo ifdown eth0
Password:
There is already a pid file /var/run/dhclient.eth0.pid with pid 5742
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:d0:59:7a:b5:b6
Sending on   LPF/eth0/00:d0:59:7a:b5:b6
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
paul@lilcomp:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:d0:59:7a:b5:b6
Sending on   LPF/eth0/00:d0:59:7a:b5:b6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.100 -- renewal in 277394 seconds.

_________AFTER________
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0


paul@lilcomp:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:D0:59:7A:B5:B6
          inet addr:192.168.2.103  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fe7a:b5b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2322 errors:0 dropped:0 overruns:0 frame:128
          TX packets:3292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1415458 (1.3 MiB)  TX bytes:462348 (451.5 KiB)
          Interrupt:11 Base address:0x8c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17846 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17846 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1626518 (1.5 MiB)  TX bytes:1626518 (1.5 MiB)

---

### Post by dcstar on 2005-12-02
[QUOTE=paulchuck]Perry-

Thanks for the response.  Here is the info you requested.  Let me know if you need anything else.
I also did an ifdown/up so you can see the output from that.
......[/QUOTE]
The only important thing I noticed is that the IP address changes after you reboot the router, this indicates to me that you are using DHCP from the router, and it may be possible that the router/PC is losing the original DHCP allocation somewhere after a period of time.

I would recommend setting up a Static IP in Ubuntu (manually entering the Router IP as the Gateway) and see if that fixes the problem.

---

### Post by paulchuck on 2005-12-05
David,

Thanks for the suggestion, can't believe I didn't think of that.  Unfortunatley, it did not work.  Same symptoms as before only now with a static IP.  It will work with the static IP but I still have to reboot the router to get anywhere.  Kind of at a loss here, so if anybody has suggestions they will be appreciated.  My roommate suggested contacting the ISP but since I am behind the router and everything else is working, I wasn't too sure about that.  Does that make sense to anybody?  Anyways, thanks and let me know if you think of anything.

---

### Post by kosmic on 2005-12-05
Hum a very strange problem, a silly question did you try another crossover cable ?

---

### Post by cwaldbieser on 2005-12-05
[QUOTE=paulchuck]David,

Thanks for the suggestion, can't believe I didn't think of that.  Unfortunatley, it did not work.  Same symptoms as before only now with a static IP.  It will work with the static IP but I still have to reboot the router to get anywhere.  Kind of at a loss here, so if anybody has suggestions they will be appreciated.  My roommate suggested contacting the ISP but since I am behind the router and everything else is working, I wasn't too sure about that.  Does that make sense to anybody?  Anyways, thanks and let me know if you think of anything.[/QUOTE]
I looked at the router manufacterer's web site, and it looks like the router keeps an internal log of what's going on.  You should try to log into the router and take a look at that to see what's going on.  Also, writing to the router manufacterer's customer support people often proves fruitful.

---

### Post by crispingatiesa on 2005-12-05
I started to have the same problem a couple days ago. My router is Dlink-DI514.

The routers log aside the regular menssages is starting to show:

 1962 04:47:04	dhcpc_input: pLeaseId NULL


with frequency.

Any clues?

I recall that Synaptic auto updateit did update some libraries a couple days ago but regrettfully I cannot remeber which?

---

### Post by -DarkMind- on 2005-12-05
what say in your /etc/network/interfaces ?



my interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

---

