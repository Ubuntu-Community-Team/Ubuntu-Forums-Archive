---
title: "networking issues :("
date: 2005-10-12
forum: Desktop Environments
---

### Post by urbanride on 2005-10-12
ok so i have networking going with the router at 192.168.0.1 and the dhcp set to 0.200 to 0.249 ... this works fine for my windows boxes but for some reason ubuntu decides to go with 192.168.15.12 ! but the internet works. But if i go static with the settings:

ip: 192.168.0.101
sub: 255.255.255.0
gate: 192.168.0.1

nothing works

help :confused:

---

### Post by rmjokers on 2005-10-12
Have you checked to make sure that your Windows boxes get assigned the correct addresses?  If they do, then can you look at the status in your router after the linux box is connected and see what it thinks is going on?

---

### Post by urbanride on 2005-10-12
yeah all the windows machines are working fine .. and they get assigned the correct dhcp stuff :mad:

---

### Post by mlomker on 2005-10-12
I'm confused as well.  They are all plugged into the same Internet connection/hub and you only have one DHCP server on your network?

Try posting the output of this:

```

sudo dhclient eth0
ifconfig eth0
route -n
cat /etc/network/interfaces
cat /etc/resolv.conf

```

---

### Post by urbanride on 2005-10-12
```
Password:
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:07:e9:56:3c:ae
Sending on   LPF/eth0/00:07:e9:56:3c:ae
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.15.1
bound to 192.168.15.12 -- renewal in 107278 seconds.
urban@ubuntu:~$

```

---

### Post by urbanride on 2005-10-12
```
urban@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:07:E9:56:3C:AE
          inet addr:192.168.15.12  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe56:3cae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7047728 (6.7 MiB)  TX bytes:833464 (813.9 KiB)

```

---

### Post by urbanride on 2005-10-12
```
urban@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:07:E9:56:3C:AE
          inet addr:192.168.15.12  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe56:3cae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7047728 (6.7 MiB)  TX bytes:833464 (813.9 KiB)

urban@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.15.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.15.1    0.0.0.0         UG    0      0        0 eth0

```

---

### Post by urbanride on 2005-10-12
```
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

```

---

### Post by urbanride on 2005-10-12
```
nameserver 192.168.0.1

```

---

### Post by mlomker on 2005-10-12
You can add multiple [ code ] blocks to a single post.

You have a DHCP server at 192.168.15.1.  I guess your first task is figuring out where that is, because your network isn't configured quite like you thought it was.

I'd try pointing a web browser at that IP address to see if it brings anything up.

---

### Post by urbanride on 2005-10-12
[QUOTE=mlomker]You can add multiple [ code ] blocks to a single post.

You have a DHCP server at 192.168.15.1.  I guess your first task is figuring out where that is, because your network isn't configured quite like you thought it was.

I'd try pointing a web browser at that IP address to see if it brings anything up.[/QUOTE]
OMG ... i just figured it out ...sorry all .. STUPID error ... i remember now that i dont have enought space on my switch... so i pluged this box into my VOIP (gateway/router) thing... which itself is pluged into my switch ... ](*,)  and the voip has its own dhcp server .... wow i am an idiot ... but than xanyway

---

