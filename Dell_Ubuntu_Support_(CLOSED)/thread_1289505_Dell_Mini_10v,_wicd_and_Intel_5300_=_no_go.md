---
title: "Dell Mini 10v, wicd and Intel 5300 = no go?"
date: 2009-10-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by inigopete on 2009-10-12
Hi, please forgive me for being a n00b. I've replaced the not-particularly-reliable Intel 1510 card that came with my Mini 10v for an allegedly better 5300. I mistakenly thought that it would "just work."

I'm running 9.04 and I replaced Network Manager with wicd because I found wicd's network management better and much faster to wake from sleep.

Is there something straightforward that I'm missing that's preventing my copy of Ubuntu from recognising this card? Whereas my previous card was recognised as eth1, ifconfig now only brings up lo and eth0, so of course wicd can't see it either.

It sounds like this guy ([http://ubuntuforums.org/showpost.php?p=5703318&postcount=1](http://ubuntuforums.org/showpost.php?p=5703318&postcount=1)) has had a similar problem, but not with my build on my computer, so I'd be interested to hear any advice you sages could offer!

Thanks.

---

### Post by inigopete on 2009-10-14
I've just realised that it wasn't an Intel 1510, it was a Broadcomm 1510 wireless card. Not sure if that makes a difference.

---

### Post by inigopete on 2009-10-15
It was as simple as realising that Ubuntu recognised the Broadcomm as eth1, but the Intel as wlan0. Setting the "Wireless interface" in wicd preferences to wlan0 was all it needed. Now working wonderfully. :)

---

