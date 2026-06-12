---
title: "Not sure what I did, Ip changes 169.254.x.x"
date: 2006-07-03
forum: Desktop Environments
---

### Post by dtruesdale on 2006-07-03
It appears it is running thru a proxy, I can't track it down. On the network I show up as 192.168.0.201 but locally the IP keeps changing 169.254.x.x about every 5 - 10 minutes. On my bcm43xx it just changes (Dell Laptop) the atheros (on the Sager) changes and drops the connection. Get's annoying. Anyone have any idea what I may have installed without knowing? Any help is appreciated.

---

### Post by christhemonkey on 2006-07-03
Do you have your ethernet devices setup to use DHCP?
That automatically reassigns ip adresses...

---

### Post by dtruesdale on 2006-07-03
I figured it out, zeroconf............ learned my lesson. It ran a proxy and showed the network my IP which was assigned static by the DHCP server for the network. Then internally on the machine it would change the IP every 5 - 10 minutes with a 169.254.x.x . Now my Sager is staying online and not dropping connections.

---

### Post by DirtDart on 2006-07-03
The 169 network is the default your NIC will take if it can't find an address via DHCP.  Basically, it gave up looking, and assigned the 169.x so it would have something.

---

