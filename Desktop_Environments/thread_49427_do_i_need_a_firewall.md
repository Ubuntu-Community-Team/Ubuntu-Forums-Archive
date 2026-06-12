---
title: "do i need a firewall?"
date: 2005-07-16
forum: Desktop Environments
---

### Post by DarkManX4lf on 2005-07-16
i have a dlink firewall router, is it really necessary forme to get a software firewall ?

---

### Post by Seti on 2005-07-16
Not really, if your D-link is already working as a firewall. Adding a software firewall on Ubuntu would just be an extra added layer of security, kinda like unnecessary padding.
Although IIRC something about D-Link their firewall is not really that good. Oh well...

---

### Post by geearf on 2005-07-16
If you have a hardware firewall no need to get a software one.

---

### Post by DarkManX4lf on 2005-07-17
thanks

---

### Post by Sav on 2005-07-20
Hi, I have a netgear router/firewall.
I don't agree with you since I tried iptables.
My firewall, theoretically, filters the icmp packets.
But if I look the iptables log, I find many icmp packets to my linux-box.

Then I tried a linksys router/firewall.
There was a great improvement, but still some packet passed.

So, I assumed that a firewall hardware is usefull, but it doesn't replace a powerfull software as iptables.
Maybe a Cisco Pix does the work, but isn't cheap at all.

---

### Post by darkmatter on 2005-07-20
[QUOTE=Sav]So, I assumed that a firewall hardware is usefull, but it doesn't replace a powerfull software as iptables[/quote]

iptables+netcat, the perfect combination.

---

