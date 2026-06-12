---
title: "random segfaults occuring"
date: 2010-10-03
forum: Desktop Environments
---

### Post by vek on 2010-10-03
So for about the last two weeks (maybe longer) I'm getting random segfaults in Ubuntu.  This happens at random to all applications (some more than others), including background services, consoles, etc, things which should never segfault.

This is new behavior, it wasn't always this way.  They show up as just a random "segfault" in the DMESG log, so often you see "such-and-such segfault..." with such-and-such being a different program each time, until something vital to the system gets hit, and the whole thing dies.  Often compiz or something like that will die and I won't notice until I try to use an effect...

In fact, I've had to reboot back to Other OS because firefox was too unstable to finish typing a post like this.  But it wasn't just firefox - everything (gwibber, wine, firefox, background python scripts, even INIT itself) can randomly die from a random segfault.

I used MEMTESTx86 and found no errors.
I can use Other OS (windows) without issue, no similar problems.  This must be new, introduced from a recent kernel or something?

This makes it impossible for me to actually use the Ubuntu partition and I have to go back to slow crappy windows to get work done, help :(

---

### Post by vek on 2010-10-03
Never mind... after a day of running Other OS, it suddenly BSOD'd also.  So I guess its a hardware problem.  Not sure what would cause random segfaults when memtest86 can do multiple full passes with zero error though

---

