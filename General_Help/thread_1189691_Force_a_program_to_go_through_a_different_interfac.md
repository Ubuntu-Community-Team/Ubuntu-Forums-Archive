---
title: "Force a program to go through a different interface"
date: 2009-06-17
forum: General Help
---

### Post by sq377 on 2009-06-17
If it's not supported in the application directly, how do I tell a program to go through a specific interface?  My default route is to eth0, but I want one program to communicate through wlan0.

Thanks

---

### Post by ericab on 2009-06-24
i have a similiar question.

using sabnzbd,
i would like it to route through eth1 for my newsservers IP address.

as of right now everything goes through eth0, even though i have both enabled...

---

### Post by The Cog on 2009-06-24
I don't think that's going to be easy. 
You need to use iptables to apply firewall-type rules to mark packets from your chosen applications. Then use custom IP routing to send those marked packets out of the interface (to the next-hop) you choose.

This tutorial gices an idea how - ignore the stuff about installing iptables (it is already there) and begin at Step 1:
[http://www.debian-administration.org/articles/379](http://www.debian-administration.org/articles/379)

Or read and understand this bible for a deeper understanding:
[http://lartc.org/howto/](http://lartc.org/howto/)

---

