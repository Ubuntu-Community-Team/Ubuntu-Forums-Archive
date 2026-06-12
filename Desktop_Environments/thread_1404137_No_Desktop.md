---
title: "No Desktop"
date: 2010-02-11
forum: Desktop Environments
---

### Post by Graham1 on 2010-02-11
Hi

Having upgraded both my computers to KDE 4.4, both now boot up with a scrambled screen (looks like screen corruption) and that's as far as I get :(. 

I can get to a working desktop by pressing Ctrl+Alt+F1, Ctrl+Alt+F7 and then logon and everything seems fine but just wondering whether this situation (on both) can be recovered or whether a restore is needed.

During both upgrades, I tried KPackageKit first and got the usual blocked updates message so chose the following commands instead (which have worked in the past for minor (i.e 4.3.x) upgrades).

sudo aptitude update
sudo aptitude full-upgrade

Any ideas?

:)

---

### Post by demimurych on 2010-02-11
Same here.

I try nvidia drivers, nv drivers, effects-off with no results.

---

### Post by demimurych on 2010-02-11
Fast fix here
[http://kubuntuforums.net/forums/index.php?topic=3109961.0](http://kubuntuforums.net/forums/index.php?topic=3109961.0)

---

### Post by Graham1 on 2010-02-12
> **demimurych said:**
> Fast fix here[http://kubuntuforums.net/forums/index.php?topic=3109961.0](http://kubuntuforums.net/forums/index.php?topic=3109961.0)

Hi demimurych

Thanks for the link :). Unfortunately, none of the suggestions fixed my problem but I have since restored from a base image and updated from that. 

Regarding my other computer (same problem), I took a full image beforehand, so I'll restore that and wait a while before upgrading again.

:)

---

