---
title: "Edgy gnome desktop slow as molasses - HELP!"
date: 2007-03-27
forum: Desktop Environments
---

### Post by gp2x on 2007-03-27
Hi all

Ive just installed Edgy on my bosses new machine and after modifying it to match mine (theyre identical spec) his desktop is still a lot slower than mine.

These are intel core duo 1.87GHz/2G/Intel 965Q machines.

Application startup is slow (rxvt takes less than a second on my machine, but takes several seconds on his, calculator likewise) and generally it appears as if the X session is running over a slow network link.

Any clues? Im completely at a loss! I need to get his desktop performing before he decides to revert to winxp :)

Thanks

---

### Post by thelinuxguy on 2007-03-28
> **gp2x said:**
> 
Application startup is slow (rxvt takes less than a second on my machine, but takes several seconds on his, calculator likewise) and **generally it appears as if the X session is running over a slow network link.**


I think your problem is identical to the one in this: [http://ubuntuforums.org/showthread.php?t=395314](http://ubuntuforums.org/showthread.php?t=395314)

No solution has been posted yet.

**Graphic card drivers?**

---

### Post by gp2x on 2007-03-28
I straced gnome-calculator starting up, and the problem appears to lie in gettimeofday calls.

     1.636178 gettimeofday({1175062734, 701204}, NULL) = 0
     1.643541 gettimeofday({1175062729, 342090}, NULL) = 0
     1.645193 gettimeofday({1175062731, 13071}, NULL) = 0
     1.647264 gettimeofday({1175062733, 34460}, NULL) = 0

Anyone know which library this is in? libc or something?

---

### Post by TURNER on 2007-03-28
Perhaps you can also try looking at this thread:

[Ubuntu freezes randomly and often]("http://www.ubuntuforums.org/showthread.php?t=322846")

it helped my sys out alot!

---

### Post by gp2x on 2007-03-28
Thanks for that.

Ive tried everything mentioned: 
* /etc/hosts is fine
* Ive tried several drivers (i810, vesa etc)
* I have plenty of swap

Im considering trying the 386 kernel. Ill let you know how I get on.

---

### Post by gp2x on 2007-03-28
I ended up installing 2.6.17-10 (as opposed to 2.6.17-11) and everything disappeared.

ie. it looks like the latest ubuntu kernel has problems

---

