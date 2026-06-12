---
title: "No internet connection"
date: 2006-07-30
forum: Desktop Environments
---

### Post by Roflcopterrr on 2006-07-30
Whenever I plug my ethernet cable into my computer, I never have a connection!

I have Ubuntu Server, and I am trying to download xubuntu, but I cannot without an internet connection!!

Please help.

---

### Post by OpsVentus on 2006-07-31
Well let's find out what's wrong then.
In terminal:
#ifconfig
#route
#cat /etc/resolv.conf

And try to ping a couple of addresses like your own ip, routers ip, internet ip.

Cheers,
Bart.

---

