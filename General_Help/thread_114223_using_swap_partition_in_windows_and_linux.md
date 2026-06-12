---
title: "using swap partition in windows and linux"
date: 2006-01-08
forum: General Help
---

### Post by randomnote1 on 2006-01-08
I came to the conclusion that when I'm running windows I have this space that I just plain can't utilize because they're specific to Linux.  I found a program that will allow windows to utilize ext3 drives, but now I want to make Windows use the swap partition for its virtual memory.  I found this tutorial 

[http://howtos.linux.com/howtos/Swap-Space.shtml#toc6](http://howtos.linux.com/howtos/Swap-Space.shtml#toc6) 

and I was curious if anybody has seen/heard anything about it and if it could be updated for use with XP.

---

### Post by Thirsteh on 2006-01-08
The swap partition isn't an ext3 partition, and I wouldn't recommend that you use it for the Windows swap as it tends to leave the swap file there through reboots and I can only dream of the consequences of that.

I don't recommend trying to access your Linux partitions from Windows or vice versa, it just never has a happy ending.

---

### Post by Khaine on 2006-01-08
It is possible, you need the swapfs driver from here

[http://www.acc.umu.se/~bosse/](http://www.acc.umu.se/~bosse/)

Follow the instructions given in the readme

---

### Post by soonindallas on 2006-01-08
That howto was written in 2002 and applies to DOS, Win 3.1 (remember that?) and Win 95/98.  I don't recall what the price of a gig of HD was in 2002, but now it seems to be about 0.5 Euro or better.

My guess is you're talking about XP which is very likely using different VM methods.

How big is your HD ?  How much is free ?  how big is the partition you're trying to make a better utilisation of ?

The risk of this kind of procedure seems to outweigh the benefit.  I would recommend splashing out on a new HD if you are that tight on disk space.

---

### Post by randomnote1 on 2006-01-08
well, I'm currently using a 40 gig drive, but that's just because I'm still in experimentation w/ Ubuntu.  I do realize what the instructions are intended for, that's why I asked if anybody knew of anything more recent.

---

