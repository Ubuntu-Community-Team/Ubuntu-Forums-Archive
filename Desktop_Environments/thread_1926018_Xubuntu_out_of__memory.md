---
title: "Xubuntu out of  memory"
date: 2012-02-15
forum: Desktop Environments
---

### Post by pellet on 2012-02-15
I installed Ubuntu 11.10 Xubuntu with lightweight XFCE window manager on my acer  (I have  1 gig RAM. and accepted 1 gig of SWAP as recommended by the install wizard )

I subsequently opened chrome browser and  opened three tabs:- gmail, facebook and twitter.

Within 24 hours the browser had been killed by the kernel and dmesg told me I was out of memory.

I upped the SWAP to 2 gigs, this time it was 4 days before the browser was killed by the kernel.

There is obviously more than meets the eye to just having a lean and mean window manager to maintain a stable system with limited resources.

I have altered swappiness and also dropping caches and do not see any  improvement .............. still out of memory after 4 days.

Has Ubuntu a kernel tuned for a modern computer with minimum of 2 Gig RAM and 4 Gig swap.? or Is it the browser being a bloat and caching without clearing up?

Methods of testing to pinpoint the problem would be most welcome.

---

### Post by snowpine on 2012-02-15
"Method of testing" is to use your favorite System Monitor ('top' is a good generic one, I think it is probably pre-installed by default) to see what is actually eating up your RAM.

If your theory is correct that Chrome is to blame, then the obvious solution is to try another browser, such as Firefox.

If you google "google chrome memory leak linux" you'll see you aren't the only one with this problem.

---

### Post by Rodney9 on 2012-02-15
All browsers have memory leaks over time, best to shut them down from time to time,

Interestingly, I can leave Chromium running for 24 hours no problem.

Rodney

---

### Post by pellet on 2012-02-15
Thanks guys for feedback

I  have been using "top" to gauge what i might do to extend the swap space and extend life of the browser and perhaps give  me a clue  as tohow to  prevent early kills of the browser by extendeding SWAP...and so far to no avail

I have also  tried firefox as well as chrome with same result.I stuck with chrome because it does have inbuilt development tools  for analysis of memory leak which I am attempting to monitor over time.

What really puzzles me though is that I have an old computer with 1/2 gig of ram  running unbuntu 7.10 gutsy gibbon  from 2007 with early  firefox (dunno what version) and it supports twenty tabs for two months no problem without closing down or reboot.

As you point out  I am not the only one with this problem but information is mighty thin on the ground to a solution

What has changed  with Xubuntu 11.10 to make it so  greedy !?

---

### Post by snowpine on 2012-02-15
Swap is very slow; my advice is to "tune" your system so that it uses swap as sparingly as possible. Basically you want to keep your total memory use under 1gb; one way to do this is to choose applications that do not have memory leaks.

If Google Chrome has a memory leak, then it is not really a Xubuntu 11.10 problem; you need to file a bug report "upstream" with Google (although if you search like I suggested, you may find someone else has already filed a bug report; you can add your comments  if you have additional details).

---

