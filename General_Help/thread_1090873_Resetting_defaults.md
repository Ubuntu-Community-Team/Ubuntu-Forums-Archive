---
title: "Resetting defaults"
date: 2009-03-08
forum: General Help
---

### Post by Zieb on 2009-03-08
I have the live version of Ubuntu running from a USB drive, and I seem to have attempted to put too much stuff on there, and am thus, out of space.  I tried downloading a ton of packages, and really don't know where to start cutting stuff out that won't screw it all up.  Thus, is there a way to tell Ubuntu that I just want it set back to the defaults (i.e. the way it was the first time I turned it on).  It won't take long to put the couple extra things I actually need back on there (Gimp, a few Mozilla updates), so I won't lose much useful stuff this way.  Any help appreciated.

---

### Post by LegendofTom on 2009-03-08
I don't think there is a way to return to default, but maybe autoremove or purge your system of the stuff you don't want.

---

### Post by Zieb on 2009-03-08
> **LegendofTom said:**
> I don't think there is a way to return to default, but maybe autoremove or purge your system of the stuff you don't want.

Ah well, I still have the live CD I used to create this USB version, so I guess I'll just wipe the USB and start over.  More time consuming, but not terribly challenging.

---

### Post by LegendofTom on 2009-03-08
Yea, I would agree that is the simplest solution.

---

### Post by tommcd on 2009-03-08
You can try booting Ubuntu, open a terminal and run:
```
sudo apt-get autoclean
sudo apt-get autoremove
```
If that does not free enough space then run:
> sudo apt-get clean
See the clean, autoclean, and autoremove sections here for an explanation:
[http://man.he.net/man8/apt-get](http://man.he.net/man8/apt-get)

---

