---
title: "IP not beeing obtained automatically at startup"
date: 2006-03-20
forum: Desktop Environments
---

### Post by TB2 on 2006-03-20
Hi,

Everytime I restart Ubuntu (dapper 5) I have to ifdown eth1; ifup eth1 so that my router gives me an IP. I also get something like .4 oder .5 instead of .2, altough I configured the router properly, to always give me .2, dependig on my MAC address. Why is that? And how do Ifix it?

Thx!

---

### Post by mlind on 2006-03-20
if that's a Dapper issue, you should post on Dapper test forums. There's been
few threads about this issue, so search them to get the details. It seems a bug.

I've experienced same issue twice, although I don't reboot often.
I usually execute *sudo dhclient eth0* to fix this.

---

