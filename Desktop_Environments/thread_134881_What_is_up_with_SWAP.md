---
title: "What is up with SWAP?"
date: 2006-02-22
forum: Desktop Environments
---

### Post by FIONEX on 2006-02-22
Hi,
I've been looking at my swap partition lately, and monitoring its activity and came to realize that linux never puts it to use.  Is it only put in use when there's no more physical memory left?  That defeats the purpose of swap entirely because then the computer will be slow.  Is there way to modify this form of memory management or is there something wrong with my settings?  I hope to god the kernel developpers are a bit smarter than that.

---

### Post by kaamos on 2006-02-22
Thats normal behaviour. Why do you think it is slower that way? I'm no expert (not even a novice for that matter) but since ram is faster to access than a hd, physical memory is faster to use than swap.

Google for linux (or unix I guess) memory management, that should get you pretty good explanations.

EDIT: evil typo.

---

### Post by FIONEX on 2006-02-22
Sorry if I seem to be arguing but I want to get a discussion going (attract a few people, lol).  Well if you think about it, having a full physical mem will be slow.  Having to transfer data from the mem to the hd in order to free up space is gonna seem slow when you need that memory.  It's always good to have enough free memory by writing data that's rarely accessed to the hd.  Windows uses TONS of memory, as we all know.  It takes about 180 mb of mem for windows to be runing in general.  However, windows quickly makes use of swap, sometimes a bit too much, but it seems effective to me.  When free memory is available for system processes, the system will perform much better, or am I wrong?

---

### Post by kaamos on 2006-02-22
> When free memory is available for system processes, the system will perform much better, or am I wrong?
Not in *nix systems. The goal in these is to use as much as ram as possible and so unused ram is seen as wasted ram.

Gonna go to bed now, I'll try to find a real explanation tomorrow. :)

---

### Post by FIONEX on 2006-02-22
I was looking at some documentation and what you said is true actually by trying to reduce disk access times.  I just realised the kswapd is running and some swap is finally being put to use (4mb out of 270 mb) lol.  I guess it only puts the really deadbeat data to rest in the swap.  Well so far ubuntu has been performing much better than redhat 8.0 use to in terms of speed.  Maybe this time I won't go back to windows.

---

### Post by ElijahLofgren on 2006-02-22
Check out:

Linux Memory Management or 'Why is there no free RAM?':
[http://forums.gentoo.org/viewtopic.php?t=175419](http://forums.gentoo.org/viewtopic.php?t=175419)

---

### Post by FIONEX on 2006-02-22
LOL I read that right before I posted that last one...I'm pro swap, regardless of what anything says, so I set the swappiness to 40 :P.  We'll see how that works for me and I'll get back to you on it later.

---

### Post by angkor on 2006-02-23
[QUOTE=FIONEX]..I'm pro swap, regardless of what anything says[/QUOTE]

Better learn to trust the experts on this. ;)

Using more swap will eventually slow down your system.

---

### Post by aysiu on 2006-02-23
Generally, I've found 512 MB of RAM or more makes swap more or less obsolete. My computer with only 128 MB of RAM uses swap all the time, though!

---

