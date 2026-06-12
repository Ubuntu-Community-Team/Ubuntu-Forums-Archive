---
title: "After upgrading physical memory, does the swap memory need to be adjusted too?"
date: 2009-01-22
forum: General Help
---

### Post by ww711 on 2009-01-22
Recently upgrade my RAM for my laptop, I'm unsure if I need to increase the size of my swap memory.

Before upgrade, 1 gig memory module and ~2 gig of swap.
Now, 3 gigs (2gig module + 1gig module), still ~2 gig of swap.


```
 free +m
```
gives
```

             total       used       free     shared    buffers     cached
Mem:          2912        968       1943          0         24        417
-/+ buffers/cache:        526       2385
Swap:         1953          0       1953

```

Should I increase the swap to 4gigs? Is this excessive? Or should I leave the configuration as it is?

---

### Post by Titan8990 on 2009-01-22
I would leave the configuration how it is because it is unlikely that you will even use the swap you have now.

It is typically best to use the same size and brand RAM modules when adding a second one. This will allow your memory to work in dual channel mode and provide a considerable performance increase.

---

### Post by malfist on 2009-01-22
I have 4 GB of RAM on my system and I hardly ever see more than 5 or 10MB of swap used. You can configure the kernal as to how swappy it is (more swappy it puts stuff in swap more often, less it will store it in ram). I've never even came close to running out of ram on ubuntu.
[http://www.brunolinux.com/06-Fine_Tuning_Your_System/Swappiness.html](http://www.brunolinux.com/06-Fine_Tuning_Your_System/Swappiness.html)

---

### Post by avtolle on 2009-01-22
You should be fine without increasing the swap, unless you want to use the hibernation feature on your laptop. IIRC, in such a case, the size of swap should then be at least equal to your RAM.

---

