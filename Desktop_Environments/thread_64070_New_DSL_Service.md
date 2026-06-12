---
title: "New DSL Service"
date: 2005-09-09
forum: Desktop Environments
---

### Post by karuptdata on 2005-09-09
So i switched from comast to qwst dsl for their new 7mb down package with one meg up...at any rate i cant seem to surf the net but the modem sinks and when i view the modem diagnostics via 192.168.0.1 i can see the ip address...however it still shows my old comast address on everything. I was wondering if there is anyway to release or flush that ip address to renew to new qwest address...

---

### Post by John.Michael.Kane on 2005-09-09
Try this  ifconfig eth0 ip.add.re.ss not sure if you need to use sudo before. or this 

1. su (to root)
2. cd /etc/init.d
3. ./network restart
4. exit (out of root)

hope this helps

---

