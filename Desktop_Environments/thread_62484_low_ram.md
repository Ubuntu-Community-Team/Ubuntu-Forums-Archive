---
title: "low ram"
date: 2005-09-04
forum: Desktop Environments
---

### Post by [pl]ice on 2005-09-04
hi, i got 768 ddr ram, and a i'm using gkrellm. after a while, over a day or so it starting to show me that my ram decreases, now i got 515 free, then tomorrow will be ~450 left, untill i restart X, i'm running always same load on pc. top shows:
Mem:    775788k total,   755792k used,    19996k free,   124420k buffers
Swap:   497972k total,     2864k used,   495108k free,   382176k cached

how can i find out what's causing it?

thanks

---

### Post by az on 2005-09-04
When something is finished with the ram, linux will not get rid of it unless it needs to.  If something else needs that ram, it will get it, so do not worry.  There just is no reason to free it for nothing.

---

### Post by rastilin on 2005-09-04
Linux will use all spare ram (minus 4MB) for caching drive operations but this is more like a memory leak in X. Thing is I've been having a similar problem, I *think* I fixed it by clocking back to the 386 kernel which is to say tha I haven't had any problems in the last day that I've been running the OS.

Please run "top" and check the memory usage of xorg. On my 512MB system it starts at 4.5% and has currently climbed up to 9.1%; I once saw it go as high as 22.5% and my whole system was agonizingly slow, everything, including nautilus and eog.

---

### Post by [pl]ice on 2005-09-05
for example, when i use firefox, then leave it o.night it eats more and more ram slowly, then close it, ram goes backup again. it just statrter not long ago, i haven't done any upgrades etc.
oh well.

---

### Post by jameswilhelm on 2005-09-05
I also have 768MB of memory on my PC and it tends to fill up over time. The up side is that applications that have already run often start up much quicker.

What you should worry about is if your swap partition starts filling up when the RAM is full and nothing else is doing much.

The offending application would be easy to catch with top or the graphical system monitor - it would be the one that uses ridiculous amounts of memory while doing nothing.

In the one case I had the gnu terminal (in Redhat) leak memory so badly that it filled up what was left of my 768MB memory plus 2GB swap space - obviously much more memory than what a terminal program needs and easily spotted in that case!

---

