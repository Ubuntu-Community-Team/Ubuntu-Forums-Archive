---
title: "Not able to connect to wire after installing wireless driver"
date: 2009-03-07
forum: General Help
---

### Post by jimerik on 2009-03-07
Hello all,

I've been using Ubuntu 8.10 since last week so I guess you can call me a newbie. After the fresh install I was only able to connect to the network via normal wire (ath0) - so I installed the Broadcom B43 wireless driver to be able to connect via my wireless router. 

But ever since I did this Im no longer able to connect via wire (ath0). When pushing the "signals" button up in the right corner in Ubuntu i get a list of all the available wireless networks but the "Wired Network ath0" connection has now become unable to choose.

I've seached for this problem but I can only find threads for how to get wireless - Id like both wire and wireless to work - especially now since Im stuck offshore on a drilling rig :)

I've tried to modify my /etc/network/interfaces. Now it just contains:

auto lo
iface lo inet loopback

I've tried to add:

auto eth0
iface eth0 inet dhcp

but then another message appears - cant remember exacly.

Is there any helpful Ubuntu wizards out there that can see an obvious solution?

Rgds,
Jim

---

### Post by x33a on 2009-03-07
run
```
sudo pppoeconf
```

---

### Post by tuskenraider on 2009-03-07
on my lappy... ive noticed that if you have wireless enabled... itll prefer wireless over the wire connection.  IDK why..seems itd be the other way around... one way  that i get around that.. is i un-enable the wireless in the network seletion tool... im at work or id tell you what thats called.   but i do that..and it finds the wired network..and badabing away we go...

maybe thisll work for you.. hope its something easy..


tusken-i like easy-raider LOL

---

### Post by jimerik on 2009-03-07
Cool - and just like that.
sudo pppoeconf did the trick.

Thanks very much.

---

