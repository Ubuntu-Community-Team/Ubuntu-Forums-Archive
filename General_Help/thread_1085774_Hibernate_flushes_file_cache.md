---
title: "Hibernate flushes file cache"
date: 2009-03-03
forum: General Help
---

### Post by Cdwijs on 2009-03-03
Hi All,

I have a lot of RAM, 2GB. I also have a swappartition of 2.9GB. Now I start a large game. The entire game, fits in 2GB (1,5GB memory used, 580MB cached). After i shutdown the game, all the gamefiles are still cached (1GB memory used, 580MB cached), so when I start the game again, there's no HD activity, and my game starts extremely fast. The swappartition is completely empty, 0KB used.

Now I hibernate my PC. After resuming I see the following:
488MB memory used, 49MB cached, 340MB swap used.

This means hibernate has flushed my filecache. Even worse, it has placed stuff into the (slow) swappartition.

When I now start the game, everything has to be loading from HD, wich is slow. 

What can I do to investigate this?
Best regards,
Cedric

---

### Post by Cdwijs on 2009-03-03
Sorry, forgot to give technical info about my machine:

Ubuntu 8.10,
Linux ce 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
Dell Vostro 1710

Best regards,
Cedric

---

