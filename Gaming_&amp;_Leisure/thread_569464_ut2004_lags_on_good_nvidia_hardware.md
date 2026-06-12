---
title: "ut2004 lags on good nvidia hardware"
date: 2007-10-07
forum: Gaming &amp; Leisure
---

### Post by fatalGlory on 2007-10-07
I've recently re-installed ut2004 on my new feisty box to practice for an upcoming LAN event at college.  I've got a pretty spiffy system but it isn't standing up to the old one - needless to say I feel cheesed.

Specs:
Core 2 Duo 4500
2Gb RAM 667MHz
256Mb NVidia 8600GTS
Feisty with automatic kernel upgrades whenever they are released

This rig should be hammering along for something as old as ut2004, I've installed the latest ut2004 patch (3369.2) and the latest NVidia drivers (100.14.19) but no dice.  I notice that the slowdown is much more apparent in certain maps, (eg. non-existent in DM-Idoma but barely playable  in DM-Albatross).

Based on some googling, I think it may have to do with Dynamic Lighting in the game, but this was never a problem before my new card and drivers so I'm assuming that one of the two (or the specific combination) has 'damaged' support for ut2004.

Any suggestions?

---

### Post by Brebs on 2007-10-07
See [thread](http://forums.gentoo.org/viewtopic-t-574123.html).

---

### Post by fatalGlory on 2007-10-07
Thanks for the link, I'd already been browsing the web.  I don't think there is currently any proper resolution to this problem, I gather its just a matter of waiting on NVidia to put out a driver for the 8xxx series cards that doesn't have this issue.

How unfortunate in the leadup to a LAN weekend

---

### Post by mikedep333 on 2007-10-07
Try disabling any desktop graphical effects if you have them enabled (xgl/aiglx.) I have seen them make 3d apps not work, become buggy, go incredibly slow, or become a little bit slower.

On Suse 10.1 for example, it made many things not start up at all or go very slow. On my gutsy laptop, it makes things go like 10% slower.

---

### Post by ravalox on 2007-11-21
I have to second this notion; it's an nvidia driver issue for the geforce8 series cards.  I have an 8800 that's causing me the same problem; the game lags periodically.  I have a laptop with much older hardware that gives me a smoother gaming experience than this!  I may attempt to use the beta drivers and see if there is any improvment; I'll update this thread again if I do.

---

