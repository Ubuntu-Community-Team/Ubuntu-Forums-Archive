---
title: "ubuntu taking 1.4gig out of 1.5 gig of ram"
date: 2006-03-28
forum: Desktop Environments
---

### Post by kasemodz on 2006-03-28
Alright, yesterday I upgraded from 768mb to 1.5 gigs on my server. Before I upgraded, when I ran top, I would usually have 50-100mb left on the ram. So I thought if I upgrade the ram, then i should have about 500mb free. Well yesterday after I booted, with all my services running, it was taking about 400mb on ram. Today, I checked and its like 1.4 gig ram used. How did that happen? I checked top and there werent many extensive ram taking programs running. Here is a screen shot. So is it actually taking 1.4 gig ram right now or what.

---

### Post by NeghVar on 2006-03-28
Linux automatically uses as much ram as possible, most is reserved in cache.

---

### Post by zenwhen on 2006-03-28
Linux is going to cache things. It does this because it is intelligent. It will use all of your available memory for cache and free it up when an application needs it. While you may "feel" better seeing that memory as free, you won’t actually be getting any benefit from it.

---

### Post by aysiu on 2006-03-28
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by Buffalo Soldier on 2006-03-28
> The reason Linux uses so much memory for disk cache is because the RAM is wasted if it isn't used. Keeping the cache means that if something needs the same data again, there's a good chance it will still be in the cache in memory. Fetching the information from there is around 1,000 times quicker than getting it from the hard disk. If it's not found in the cache, the hard disk needs to be read anyway, but in that case nothing has been lost in time.

During my earlier years using computer, I too have this misconception that the system RAM should be "free" :P

It took a while for me to understand the paradigm that resources are there to be used and not be sitting idle.

---

### Post by kasemodz on 2006-03-28
thanks, I understand it now.

---

