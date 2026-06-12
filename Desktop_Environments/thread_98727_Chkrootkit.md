---
title: "Chkrootkit"
date: 2005-12-04
forum: Desktop Environments
---

### Post by Gray. on 2005-12-04
Sorry if this seems silly, but I just recently installed chkrootkit and when I ran it, it came up with everything not infected/not found except I got this one line which has me a bit worried:
```
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
**eth0: PACKET SNIFFER(/sbin/dhclient3[6879])**
Checking `w55808'... not infected

```
I'm running bpalogin which I need to connect to the internet, maybe that's what this "packet sniffer" is, because I use DHCP to get an IP.
Any help greatly appreciated.

---

### Post by towsonu2003 on 2005-12-04
no worry. that's the dhcp thing... dhclient basically gets you a new ip from dhcp server... legitimate, as long as you know you are using it to get ip :)

---

### Post by Gray. on 2005-12-04
Thanks! My paranoia is slightly lowered now...... lol

---

