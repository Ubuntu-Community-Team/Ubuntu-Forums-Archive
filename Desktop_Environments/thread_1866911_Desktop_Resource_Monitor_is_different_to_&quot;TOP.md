---
title: "Desktop Resource Monitor is different to &quot;TOP&quot;?"
date: 2011-10-22
forum: Desktop Environments
---

### Post by elliotlo on 2011-10-22
It showed "120MB" for used RAM, but "TOP" and "free -m" showed a larger one.
How come please?

---

### Post by tom4everitt on 2011-10-22
Hi, I don't know about Desktop Resource Monitor, but I compared top with System Monitor (installed by default), and they did far from agree. 

I think it is like this: top reports how much ram is actually free, i.e., is not used (I checked, and top agrees with /proc/meminfo - run top and 'watch cat /proc/cpuinfo' in parallel terminals, and you'll see they agree). So in that sense top is right. 

However, part of this RAM usage is actually just caching of hard drive data, and is only used for that as long as no other program needs the space (to speed up file reading). So one could argue that the RAM usage reported by top is correct, but not entirely relevant. The System Monitor program probably only reports RAM used by *programs*, and considers the rest as free. 

This little theory of mine is strengthened by the fact top and System Monitor agreed pretty well right after boot, but as I used the system they would diverge more and more - presumably because more and more data where cached in RAM. I also remember reading about this once, but I don't remember where. 

Perhaps someone else could verify this.

---

