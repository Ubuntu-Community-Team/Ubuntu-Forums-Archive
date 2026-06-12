---
title: "Can not connect to WAN"
date: 2006-05-28
forum: Desktop Environments
---

### Post by TTT_travis on 2006-05-28
Hello,
I recently bought a new router the other day (Linksys WRT54GC) it was working great , yesterday I was surfing on my mac that connects to my ubuntu box that I use as a proxy for caching etc. with squid, and my pages stopped loading nothing was working. So later I sshd into my ubuntu box and ran ifconfig, it seemed to be able to get an ip fine, I tried pinging sites that was working but when I tried todo pretty much anything else, like apt-get update it wont connect. I tried rebooting and messing around but still can not figure out what the problem is, I dont think its related to squid but maybe it is?

Any help would be much appreciated,
Travis

---

### Post by TTT_travis on 2006-05-28
Oh, and my box works fine for things inside the network, the box just can't connect to anything outside. I also checked the firewall stuff on my router and it all seems to be disabled, at this point I have no clue whats causing it.

Travis

---

### Post by jones_jj on 2006-05-28
I am assuming your Ubuntu box is not able to connect out to the outside world?  Are you on a cable or DSL connection?   Also have you checked your network settings on the Ubuntu box to see if anything has changed?

With your old router, were you using Ubuntu as a proxy using Squid?  And it worked correct?  So if nothing has changed on your Ubuntu box it may not be Squid.  Unless, what router were you using before you got your new one?  I know Linksys routers tend to use 192.168.1.x and other routers use 192.168.0.x you may need to change something in Squid to match the internal addressing that Linksys uses.

---

### Post by TTT_travis on 2006-05-28
[QUOTE=jones_jj]I am assuming your Ubuntu box is not able to connect out to the outside world?  Are you on a cable or DSL connection?   Also have you checked your network settings on the Ubuntu box to see if anything has changed?

With your old router, were you using Ubuntu as a proxy using Squid?  And it worked correct?  So if nothing has changed on your Ubuntu box it may not be Squid.  Unless, what router were you using before you got your new one?  I know Linksys routers tend to use 192.168.1.x and other routers use 192.168.0.x you may need to change something in Squid to match the internal addressing that Linksys uses.[/QUOTE]

Yes, I can't connect to the outside world. I am on a cable connection. I have tried changing some network settings but nothing seems to help. I was using Ubuntu as a proxy using Squid with my old router, and also for about a day or 2 on my new router. My routers IPs were always 192.168.1.X. I will check the squid settings, to see if maybe something in there is messing up, since squids installed on the box does all network connections go through it or no?

---

