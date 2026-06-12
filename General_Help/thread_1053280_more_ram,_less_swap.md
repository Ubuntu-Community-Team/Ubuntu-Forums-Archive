---
title: "more ram, less swap"
date: 2009-01-28
forum: General Help
---

### Post by birnam on 2009-01-28
First off, I'm a recent Vista convert *does happy Linux dance* so while I've gained a lot of ground in the last four weeks, there are plenty of obvious things I just don't know yet, and plenty more that are just so different from WindowsWorld that I don't recognize it as 'correct.' Maybe this is one...

I'm having trouble getting Ubuntu (8.10 x64) to use all of my RAM. I have 6GB on my system. My RAM usage just peaked at the highest I've seen since installation at 59%. System monitor is reporting 3.4 GiB of 5.8 GiB of my Memory is being used. And 2.6 GiB of 15.9 GiB of Swap is being used. 

Shouldn't more of my memory be used up before the swap gets that high?

I'm running VMWare Workstation with a Vista VM running with a dedicated 2.5GB (set to reserve the memory), Apophysis (via Wine) has allocated 2.1GB for a render, I'm running Gimp, three or four different browsers (not multiple windows, multiple actual browsers), thunderbird, and various smaller applications. It's a testament to Linux that my system is running as smoothly as it is. But it just doesn't seem to be using my memory optimally.

This may just be me coming from WindowsWorld, but I consider optimal memory use to be when all available RAM is used! I can see that maybe it's good to keep a few hundred megabytes available to make launching new apps/windows smoother, but I don't know why it's hanging on to 2.3GiB!

Are my expectations off, or what?

---

### Post by jerome1232 on 2009-01-28
Now I don't know if this is what's doing it but I know gimp maintains a tile cache in ram, it has a set amount that it'll keep there, if it exceeds that set amount of tile cache then it'll use swap.

Linux does actually use all of the ram that's available, if it's not being used by applications it's being used as a file cache.


for example on my (much more modest) system you'll see that of 1000 MB's, 983 MB's are being used, 317 MB's of it is being used as a file cache, 660 MB's of it is being used by applications, the system monitor only shows the amount used by applications. My swap was at 39 MB until I opened gimp :) Which is why I just think gimp likes to use swap.

```
             total       used       free     shared    buffers     cached
Mem:          1000        983         16          0          5        317
-/+ buffers/cache:        660        339
Swap:         2047        222       1825

```

---

### Post by oldos2er on 2009-01-28
You can set swappiness by adding "vm.swappiness=x" (where x is a number between 0 and 100) to /etc/sysctl.conf. I have mine set to 5. If you set it to 0, swap is turned off. 

 Here's more info on swap: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by birnam on 2009-01-29
Awesome tip, oldos2er! I found out that Ubuntu sets swappiness to 60 by default. I reset it to 10. I'm not running as much (yet) today, but right now my stats are 2.4GiB/5.8GiB for memory, and 6**MiB**/16GiB for swap, which looks exactly right to me!

Many thanks!

---

