---
title: "SOLVED: Slow Booting because of usplash"
date: 2008-01-31
forum: Desktop Environments
---

### Post by unbuntued on 2008-01-31
Hey folks,

I'm running Ubuntu on my Toshiba M70 Satellite. One problem I was facing is the insane boot time (and the fact that no text was displayed during the boot), it took about 180 seconds to  boot (that's 3 minutes!!). After investigating using bootchart, and checking some forum posts, I found out that usplash might be causing the problem (see attached bootchart image).

I uninstalled uspash by doing:
```
sudo apt-get remove usplash
```

Result, I now boot in about 31 s (that's 6 times faster) and I can see what's going on behind the scene (see second attached bootchart image).

Two things:
1- If you're facing a similar problem, maybe this can help you.
2- Do I have to report this bug somewhere? What do i need to mention in the bug report?

Thanks

---

