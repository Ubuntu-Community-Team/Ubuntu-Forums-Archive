---
title: "Memory Optimizer for Ubuntu?"
date: 2006-01-19
forum: General Help
---

### Post by cooldudejz on 2006-01-19
are there any memory optimizers for ubuntu/linux. something like this for xp [http://www.download.com/Memory-Optimizer/3000-2086_4-10145323.html?tag=lst-0-5](http://www.download.com/Memory-Optimizer/3000-2086_4-10145323.html?tag=lst-0-5).
if there are can anyone recommend me one. thanx

---

### Post by jag164 on 2006-01-19
Honestly, even in the Windows world products like that are rather gimmicky.  They really don't do all the good they claim they do.   To that point, you won't find anything like that in the linux world.   If a mem managment and/or optimization routine proved worthy its already been integrated into the linux kernel.  No third party applications will do those type of optimizations. 

Now if you just want to identify memory hogg-ish programs and the like, from the menu choose *_Applications->System Tools->System Monitor_* and that will show you all kinds of good stuff.

---

### Post by veloct on 2006-01-20
The only thing you really could add is install powertweak which optimizes many operations in linux.  I can't say if it would be a huge improvement but linux handles things like that much better than windows does.  It's in the repo's if you want to give it a shot.

---

### Post by chaumurky on 2006-01-20
If your memory's not full of cache it's wasted... ;-)

---

### Post by engla on 2006-01-20
[QUOTE=chaumurky]If your memory's not full of cache it's wasted... ;-)[/QUOTE]
Yes, this is very interesting. 

Previously my machine had 128 M, and everything went sloooowly, the memory was used to its fullest.

Right now I've upgraded to 320 M, and everything is much much better. However, system profiler (whatever it is called) reports that I typically use 150 M of memory (resident, I think). I'd of course like all my apps to use all of it -- but I assume that with my current setup, all the apps get what they ask for, that's it.

I mean, most apps are made to effectively use its resources, and ask for only what they need -- but I was under the impression that on Linux and OS X, we had a system that enabled us to really use ALL the memory available.

Basically, my imaginations come from rumours that I've heard, along the lines of (for example) that the kernel uses extra memory to map commonly accessed parts of the HD. True or false?

So basically, I request that some low-level applications use more memory in a way you can compare to the nice system. HD-mapping would be very nice and just release its memory whenever, say firefox needed it.

Also- I don't know how close Xorg is to double-buffering its windows, but perhaps that would be possible too.

[Okay, this was a rant, but again, it's interesting.]

---

