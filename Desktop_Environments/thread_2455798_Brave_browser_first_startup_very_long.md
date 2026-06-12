---
title: "Brave browser: first startup very long"
date: 2020-12-28
forum: Desktop Environments
---

### Post by Hagar Delest on 2020-12-28
Hi,

Since not long ago (cannot tell exactly when I noticed that), the time for the first launch of the Brave browser is quite long (20 s). When using a brand new profile, it is still 15 s. This occurs only at the first launch. The following ones are almost immediate.
My Brave version: 1.18.75 Chromium: 87.0.4280.101 (Build officiel) (64 bits).
My machine is a brand new laptop with xubuntu 20.10. It's an HP with (per lscpu) a AMD Ryzen 7 3700U with Radeon Vega Mobile Gfx. And 16MiB RAM.
The system (including home) is on a SSD drive but the Brave profile on a hard drive. But this configuration hasn't changed at all compared to the time it used to work fine.
I remember a new Brave version update some days ago but I think it appeared before, but not sure it was at the previous version upgrade.

Thanks!

---

### Post by T6&amp;sfpER35% on 2020-12-28
mine does exactly the same , doesn't bother me i'm just putting it down to RAM

---

### Post by CatKiller on 2020-12-28
Have you installed Brave as a snap? Longer initial startup is one of the current downsides of snaps.

---

### Post by Hagar Delest on 2020-12-28
Brave installed with the repositories, no snap.

---

### Post by bigmeme2 on 2020-12-28
What is the speed of your hard drive? This may be the issue, especially since the things you are doing usually involve a lot of reading and writing in the background. Otherwise it is probably an issue with the brave update. Maybe roll back the update?

---

### Post by CelticWarrior on 2020-12-28
> [COLOR=#000000]The system (including home) is on a SSD drive but **the Brave profile on a hard drive**.[/COLOR]

This will certainly slow it down. By how much? it depends. At first it may not even be noticeable but as time goes by and user addons and navigation data piles up the slowdown will be noticed, of course.

---

### Post by Hagar Delest on 2020-12-29
> **bigmeme2 said:**
> What is the speed of your hard drive? This may be the issue, especially since the things you are doing usually involve a lot of reading and writing in the background. Otherwise it is probably an issue with the brave update. Maybe roll back the update?
No idea. I don't think it's relevant. First it's a brand new laptop (3 weeks old) and second, following launches are almost immediate. Something may remain in memory to speed up following launches but did not manage to find anything of the kind in top or task manager.
I'd like to roll back one or two versions. Did not find any download link after a quick search but worth another try. Will do.

> **CelticWarrior said:**
> This will certainly slow it down.
In fact, when I tried with a brand new profile, I deactivated the symlink to the HD. Thus the new profile was created on the SSD partition. But almost no change. It went from 20s (HD) to 15s (SSD).

For the record, only 3 extensions installed: speed dial, smartUp Gestures and Paste From Context Menu. So no big deal when initializing.

---

### Post by ActionParsnip on 2020-12-29
What is the output of
```

ls /snap/*

```
Thanks

---

### Post by Hagar Delest on 2020-12-29
ls /snap/* gives: /snap/README (:roll:)

I tried a Brave nightly build (1.18.25) and there is some improvement (startup reduced to 12s).
But there is still something that has changed I think. Brave must keep something in the cache. When I clear the cache (sync; echo 1 > /proc/sys/vm/drop_caches), I get the long startup time again.

I went from Firefox to Brave because of the long starting time of FF several months ago, I tried again FF and it opens in less than 3s now!
So, back to Firefox...
I don't tag the topic as solved because it's not at all, it may interest those using Brave.

---

### Post by dino99 on 2020-12-29
Glance at 'journalctl -b | grep Brave' output into a terminal, and pay attention to red lines (errors) too.

---

### Post by Hagar Delest on 2020-12-29
Nothing comes out of that.
I cleaned the memory cache, launched Brave and had a look at the (whole) log limited to the few minutes around that action but nothing related to Brave. Not really surprising, it seems that it's just taking time to initialize the application.

---

