---
title: "update =&gt; kernel panic"
date: 2005-05-25
forum: Desktop Environments
---

### Post by hulkie on 2005-05-25
Hello,
Yesterday I updated my system and this included installing a new kernel (2.6.10-5-686-smp the default kernel for a 686 hyperthreading computer) and upon restarting today, the computer will not boot anymore; After reaching 'Starting Ubuntu' I get the following error message:

/sbin/init: 395: arith : syntax error: "0xv/hda5"
kernel panic - not syncing : Attempted to kill init!

I might add here that hda5 is my swap partition.

I read several other posts on the forum about kernel panics after upgrading today or yesterday but none had the same error message; in the other posts something like 'Not syncing: VFS: unable to mount root fs on unknown-block (0,0)' was displayed, which was not the case for me.  

Through the use of the live-cd I managed to install different kernels through apt-get which are displayed correctly in grub (which was suggested to work on other posts) but exactly the same result.

Hope someone can find the solution because I really don't want to start burning dvd's..

---

### Post by Burgundavia on 2005-05-25
Can you file a bug for this?

In the summary mention the specific problem, so that it does not get marked as a duplicate of the other issues.

bugzilla.ubuntu.com

Corey

---

### Post by KingBahamut on 2005-05-26
Hmmm, Id venture that recompiling yourself rather than doing so through apt-get to get a kernel in the state you want it to be. Ive never had success with getting kernel through apt-get , however I suspect that it might be a bug, and Id report it.

---

### Post by cutOff on 2005-05-26
Did you see this [thread](http://ubuntuforums.org/showthread.php?t=36573) ??

---

