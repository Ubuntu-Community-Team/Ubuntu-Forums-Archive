---
title: "vpnc loses routing on reconnect."
date: 2006-01-15
forum: General Help
---

### Post by FishFoot on 2006-01-15
Hi Guys,

I'm having a strange routing problem.  Today I discovered vpnc, the vpnclient for connecting to cisco routers.  It is exactly what I've been looking for.  I got it up and running with some minor effort and all was going fine... that is until I shut down the vpn and then restarted it.  Once restarted I can't ping anything off my local network.  When I run 
```

route

```
the command hangs, or takes forever to display routing info.  I've been through this before and I've learned that it may be a DNS problem, which makes sense because with vpnc active I'm using my corporate DNS server.  So I run
```

route -N

```
and I get the following output:
```

FishFoot@lappy:~$ route -N
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
a.a.a.a       192.168.1.1     255.255.255.255 UGH   0      0        0 eth1
192.168.128.2   0.0.0.0         255.255.255.255 UH    0      0        0 tun0
192.168.128.4   0.0.0.0         255.255.255.255 UH    0      0        0 tun0
192.168.128.0   0.0.0.0         255.255.255.0   U     0      0        0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

```
where "a.a.a.a" is the address of my vpn server.  Incidentally, when everything is working correctly I get the exact same routing info from route, but instead of the IP Addresses I get the DNS resolved names.

Anyway, this was frustrating me, but I've discovered that if I shutdown the vpnc connection and then close the terminal I'm in, then I open a new terminal and start the vpnc connection everything works again.

Now this is only moderately annoying, but more importantly I'd like to know what is going on... any ideas?

---

### Post by FishFoot on 2006-01-15
I don't think this is what's actually happening... forget this thread its junk.

---

