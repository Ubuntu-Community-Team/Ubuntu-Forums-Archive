---
title: "dell 1545 core2duo wireless issues"
date: 2012-06-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by linuxaddix on 2012-06-23
i have a dell 1545 core 2 duo dual boot with win7 and kubuntu12.04 only problem is i cant get wireless on my kubuntu.i believe i have a bcm4312 card.ive tried downloading the sta card from bcm with not a clue on how to install it on kubuntu.i am not a newbie with linux but ive stopped using it for awhile and now i need refresheners.please help me get my wireless working.thanks in advance.
and btw i have no ethernet access either.i need an offline method.

---

### Post by blackflame2996 on 2012-06-24
plug in to LAN, and find the additional drivers settings menu. If it finds a driver, install it. if not, post back

---

### Post by linuxaddix on 2012-06-24
blackflame thanks for the response but i have no ethernet access as ive mentioned.im using wifi from my windows installation.i need an offline method.

---

### Post by wildmanne39 on 2012-06-26
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```

---

