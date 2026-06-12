---
title: "Permanent static routes?"
date: 2006-01-09
forum: General Help
---

### Post by JohnnyPrimus on 2006-01-09
I've added a couple of static routes via "/sbin/route add" and my packets are happily being routed, however if the box reboots these will need to be manually added again.

How can I make this permanent?  After a bit of research it seems like /etc/network/interfaces is the solution to this, but I'm unclear as to how the syntax works for that file.  Any Ubuntu/Debian networking gurus that can help?  The kernel's routing table appears below.


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.128.0.0      *               255.255.255.0   U     0      0        0 eth0
172.16.0.0      10.128.0.1      255.240.0.0     UG    0      0        0 eth0
10.0.0.0        10.128.0.1      255.0.0.0       UG    0      0        0 eth0
default         serverfw.xxx. 0.0.0.0         UG    0      0        0 eth0


grazie mille,
JP

---

### Post by ranf on 2006-01-09
"man interfaces" pointed me to:
/usr/share/doc/ifupdown/examples/network-interfaces

Hmm, file not found. But there is one with .gz 
```
zless /usr/share/doc/ifupdown/examples/network-interfaces.gz
```

Hit the `/' key and search for route.

---

### Post by dcstar on 2006-01-09
[QUOTE=JohnnyPrimus]I've added a couple of static routes via "/sbin/route add" and my packets are happily being routed, however if the box reboots these will need to be manually added again.

How can I make this permanent?
......[/QUOTE]
One way is to make a script in /etc/init.d with your "route add ......" commands and have it run at startup.

---

### Post by cylon359 on 2006-01-09
You could also have a routing daemon such as quagga installed, and tell it all about your static routes

---

### Post by JohnnyPrimus on 2006-01-10
[QUOTE=ranf]"man interfaces" pointed me to:
/usr/share/doc/ifupdown/examples/network-interfaces

Hmm, file not found. But there is one with .gz 
```
zless /usr/share/doc/ifupdown/examples/network-interfaces.gz
```

Hit the `/' key and search for route.[/QUOTE]


Brilliant this is exactly what I needed.

Thanks for the other ideas as well fellas I appreciate it.

---

### Post by rapha on 2006-04-05
Same problem here... I tried putting the following into my /etc/network/interfaces, but the route doesn't come up...

```
auto eth2
iface eth2 inet static
  address aaa.bbb.ccc.ddd
  netmask 255.255.255.0
  gateway aaa.bbb.ccc.eee
  up route add -net 192.168.173.0 netmask 255.255.255.0 gw 172.27.254.254 dev eth0
  down route add -net 192.168.173.0 netmask 255.255.255.0 gw 172.27.254.254 dev eth0

```

What am I doing wrong?

Regards,
Raphael

---

### Post by dcstar on 2006-04-05
[QUOTE=rapha]Same problem here... I tried putting the following into my /etc/network/interfaces, but the route doesn't come up...

```
auto eth2
iface eth2 inet static
  address aaa.bbb.ccc.ddd
  netmask 255.255.255.0
  gateway aaa.bbb.ccc.eee
  up route add -net 192.168.173.0 netmask 255.255.255.0 gw 172.27.254.254 dev eth0
  down route add -net 192.168.173.0 netmask 255.255.255.0 gw 172.27.254.254 dev eth0

```

What am I doing wrong?

Regards,
Raphael[/QUOTE]
Possibly you should test the full route command externally to ensure that it actually works as you intended.

Secondly, perhaps the "post-up" prefix is more appropriate than "up"?

---

### Post by rapha on 2006-04-06
> **dcstar]Possibly you should test the full route command externally to ensure that it actually works as you intended.[/QUOTE]

Wouldn't have posted here without have tried the route on the commandline first  said:**
> Secondly, perhaps the "post-up" prefix is more appropriate than "up"?

Why does the documentation (zless /usr/share/doc/ifupdown/examples/network-interfaces.gz) say otherwise then? Also, it doesn't at all mention "post-up". I still tried it though, and it doesn't bring the route up either.

---

### Post by dcstar on 2006-04-06
[QUOTE=rapha]Wouldn't have posted here without have tried the route on the commandline first ;-)



Why does the documentation (zless /usr/share/doc/ifupdown/examples/network-interfaces.gz) say otherwise then? Also, it doesn't at all mention "post-up". I still tried it though, and it doesn't bring the route up either.[/QUOTE]
Try moving the commands into a script in the /etc/network/if-up.d directory.

---

### Post by rapha on 2006-04-06
[QUOTE=dcstar]Try moving the commands into a script in the /etc/network/if-up.d directory.[/QUOTE]

Gees, that did it! Thanks a heap dcstar!

---

