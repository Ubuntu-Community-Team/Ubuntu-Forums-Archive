---
title: "Mysterious boot with linux-686"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Jayschwa on 2006-08-18
Hello, I'm having a bizarre problem, and I was wondering if someone might have an idea as to what it could be.

I have a P4 w/HT, so I figured I should use the 686 kernel. When I get it though, boot-up becomes unstable and inconsistent for me. About 1/5 of the time, I can get into Ubuntu fine, with no further problems. About 2/5 of the time, the loading screen is reached, and it will hang on something like "Mounting Filesystem" (the second line that pops up). The other 2/5 of the time, it will get past grub, but before the loading screen, then just restart. It posts again and starts over.

Now, I haven't had trouble with any other distros and optimized kernels, I have no problem with the ubuntu 386 kernel, and I have no problems once I get passed the loading screen with 686. It has me scratching my head, mainly due to the inconsistency of it. Some days it'll go first try, and other days it tries five times before it finally succeeds.

I'm guessing there isn't much I can do about the problem, whatever it is, but I was wondering if anyone here has seen anything like this before or might have some speculation as to what it could be.

Cheers,
Josh

---

### Post by BitTorrentBuddha on 2006-08-18
That is very odd, where exactly does it stop when running boot processes. Try installing linux-686-smp instead, smp is optimized for dual cores and hyper threading.

---

### Post by Jayschwa on 2006-08-18
It does the same thing. As far as I know linux-686 and linux-686-smp use the same packages.

It hangs either when it mounts the filesystem, or right when the boot screen loads (just the ubuntu splash), and sometimes it just restarts before the load screen appears (right after the grub text).

---

### Post by justinchudgar on 2006-08-24
I've got the same problem. Dapper and Edgy both work fine with the default 386 kernel, but I cannot boot into the linux-686-smp kernel that I installed via apt-get.

The 2.6.15 and 2.6.17 (dapper and edgy) and  a 2.6.17 make-kpkg custom P4-SMP kernel all stop at the "Mounting root file system..." stage. This has happened a dozen or more times with variations on the theme, ubuntu, kubuntu, dapper, edgy, custom, etc.

I like ubuntu, but, I paid for my 2 cores and really want to use them. Help.

---

