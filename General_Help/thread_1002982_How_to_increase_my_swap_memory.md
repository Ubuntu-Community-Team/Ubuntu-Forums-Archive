---
title: "How to increase my swap memory?"
date: 2008-12-05
forum: General Help
---

### Post by stmartin on 2008-12-05
Since I installed Ubuntu I realized that when I play videos on [www.youtube.com](www.youtube.com) they are "freezing" on every second. Is this consequence of my swap memory? I don't know how much swap memory did I set up, but I got 2 GB RAM memory. How to increase my swap memory?

Thanks in advance.

---

### Post by taurus on 2008-12-05
I doubt it's your memory.  Could be either java or flash.  If you want to know about how much swap partition you have, just run

Applications -> Accessories -> Terminal
```
free -m
```

---

### Post by kerry_s on 2008-12-05
> **stmartin said:**
> Since I installed Ubuntu I realized that when I play videos on [www.youtube.com](www.youtube.com) they are "freezing" on every second. Is this consequence of my swap memory? I don't know how much swap memory did I set up, but I got 2 GB RAM memory. How to increase my swap memory?

Thanks in advance.

i very much doubt it's your memory, i only have 256mb and mine play fine.
you could have something wrong with yours, first try uninstalling it and reinstalling it. if that don't work, you might have the pulse audio problem(sound) do a search of the forum for the fix.

---

### Post by stmartin on 2008-12-06
Thanks for the posts.
I got:
stmartin@stmartin-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2026        820       1206          0         47        417
-/+ buffers/cache:        355       1671
Swap:          878          0        878

Do this means that 355MB ubuntu is taking in background?

---

### Post by kerry_s on 2008-12-06
> **stmartin said:**
> Thanks for the posts.
I got:
stmartin@stmartin-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2026        820       1206          0         47        417
-/+ buffers/cache:        355       1671
Swap:          878          0        878

Do this means that 355MB ubuntu is taking in background?

your memory's fine, your swap is fine.

---

