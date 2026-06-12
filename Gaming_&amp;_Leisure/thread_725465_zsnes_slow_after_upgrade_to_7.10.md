---
title: "zsnes slow after upgrade to 7.10"
date: 2008-03-15
forum: Gaming &amp; Leisure
---

### Post by rossjman1 on 2008-03-15
I have a pretty old computer, that I'm using to hook up to a tv to play emulators on. Before upgrading to Ubuntu 7.10, ZSNES was running at a decent speed, but after the upgrade it's unplayable. Is there a fix for this or some ZSNES options that will make it run faster?

---

### Post by dfreer on 2008-03-15
Might be helpful if you give us more specs about your computer (specifically video card, RAM, processor specs).

---

### Post by rossjman1 on 2008-03-15
Further inspection shows that my entire computer is slow after the upgrade. A process called udevd is using 100% cpu usage.
I did some googling and did this: which seemed to fix it.
```

sudo apt-get remove evms
```
However, when I try to run Zsnes from MythGame it launches but immediately closes even though it works perfectly in GNOME.
```

zsnes -v 4 %s
```

---

### Post by dfreer on 2008-03-15
Try running it in terminal, and see if it crashes. If it does crash, see if it left any meaningful output in terminal.

If it doesn't crash, I'd suspect it has to do with the way you set up MythGame.

---

### Post by rossjman1 on 2008-03-15
It works in GNOME, and I haven't changed any settings of mythgame since the upgrade, and it was working before... ZSNES doesn't crash.

---

### Post by rossjman1 on 2008-03-16
Well, I tried launching MythTv Frontend from my username jeff, and running zsnes works the way I wanted it to, so I copied the ~/.zsnes folder from my jeff user and pasted over the mythtv user's version.

---

### Post by dfreer on 2008-03-17
Glad you figured it out. Always gotta watch out for those absolute paths/relative paths. :D

---

