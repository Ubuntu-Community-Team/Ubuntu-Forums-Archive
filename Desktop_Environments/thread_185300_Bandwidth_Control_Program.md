---
title: "Bandwidth Control Program?"
date: 2006-05-31
forum: Desktop Environments
---

### Post by Indiana Red on 2006-05-31
I am looking for ways to set bandwidth quotas on my XP boxes on my home LAN.  I have an UBUNTU box running on this network as well and am wondering if there is a program I can run that could help me manage this.
Basicaly throttle down the kids PCs and leave wide open my UBUNTU and my main Xp box that I game on etc.
I know that managed switches can do this but I don't think I can justify that kind of equipment on my home network.
Any Ideas?

---

### Post by 23meg on 2006-05-31
You should look into wondershaper and trickle, both of which should be in the repositories.

---

### Post by DarthMandeep on 2006-05-31
Unless you're using the Ubuntu box as a router, I'd suggest looking into buying a Linksys WRT54GL or the WRT54SLGS, a low cost router/switch/wifi device that runs Linux. You can load firmware like Thibor's HyperWRT and use QoS to give your computers priority over other machines on the network. 

QoS lets you specify which computers and which ports should have their packets sent out first, which can help improve latency in games, and also prevent bittorrent from slowing down the entire network. This is also useful if you're a voip user and you want your phone connection quality to improve.

---

### Post by Rizado on 2006-06-05
[QUOTE=DarthMandeep]Unless you're using the Ubuntu box as a router, I'd suggest looking into buying a Linksys WRT54GL or the WRT54SLGS, a low cost router/switch/wifi device that runs Linux. You can load firmware like Thibor's HyperWRT and use QoS to give your computers priority over other machines on the network. 

QoS lets you specify which computers and which ports should have their packets sent out first, which can help improve latency in games, and also prevent bittorrent from slowing down the entire network. This is also useful if you're a voip user and you want your phone connection quality to improve.[/QUOTE]Well QoS works on a linux router as well, if not better than a normal router...

---

### Post by Indiana Red on 2006-06-05
Interesting, Thanks.
Yes, Bittorrent, Games, Packet Priority are all factors I am loking at.  I am resisting swapping out my Actiotec DSL Router as it is working well enough for me but will lookinto the Linksys options you mentioned.  I have had goood experiances with their stuff in the past including the 2 WAPs I am using now on this same network.

---

### Post by DarthMandeep on 2006-06-06
[QUOTE=Rizado]Well QoS works on a linux router as well, if not better than a normal router...[/QUOTE]

The routers I suggested are running Linux. I wouldn't suggest anything else :)

---

### Post by jones_jj on 2006-06-07
Actually if you're running XP, QoS is already built into XP under properties of your NIC.  It is turned on by default.  You may want to look into this also.  I belive most SOHO routers today have some sort of QoS built into them and or bandwidth throtling.  I belive my Netgears do, but I'm not totally sure about that, since I don't have to worry about PCs taking to much bandwidth.

But free is always better than having to buy something, so look at the tools you already have at your disposal.

---

