---
title: "How to boot amd64 livecd on 965 chipset?"
date: 2007-03-18
forum: Development CD/DVD Image Testing
---

### Post by UBfusion on 2007-03-18
I am still stuck with bug #84964 and cannot boot the 0317 amd64 livecd on my Asus P5B-VM (and most people with 965 chipsets can't even boot from HD if using the newest kernels).

Unfortunately, comments and workarounds found on the bug threads pertain to an already installed feisty, so I wonder if there a way to modify the live CD's booting sequence to insert some of the suggested parameters and experiment if they work. Any help is much appreciated.

PS. This build works beautifully as a guest in VMware.

---

### Post by MattiJ on 2007-03-18
Me to wonder this, Can't boot this on asus P5B, tried to flash new bios but this wont help. Using Edgy now but wanted to test 64bit and maby install it on another partion.

[http://www.ubuntuforums.org/showthread.php?t=335564&page=3](http://www.ubuntuforums.org/showthread.php?t=335564&page=3)
I gona try rsynk...

---

### Post by Henrik on 2007-03-19
Seem the fix for this was released yesterday:

[https://beta.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964/+activity](https://beta.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964/+activity)

Please try today's daily build and see if you can confirm that.

---

### Post by UBfusion on 2007-03-19
Thanks Henrik will certainly try today. The bug activity link you provided is restricted but I will report results in the bug thread.

---

### Post by MattiJ on 2007-03-19
Nope just testing "Ubuntu 7.04 "Feisty Fawn" - Alpha amd64 (20070319)" but it wont boot.
it stay with modeprobe abnormal exit.

---

### Post by UBfusion on 2007-03-19
No joy here either :-(

Tomorrow is another day...

---

### Post by Henrik on 2007-03-19
> **UBfusion said:**
> Thanks Henrik will certainly try today. The bug activity link you provided is restricted but I will report results in the bug thread.


Ah, sorry I kee doing that. It's just the beta. link. This one works:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964/+activity](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964/+activity)

---

### Post by UBfusion on 2007-03-20
0320:    No progress on today's build (0320), I posted comment on the bug thread :(

0320.1: No changes in 0320.1 also released today

0322:    Today's rebuilt amd64 live iso (0322) did not fix bugs #84964 and #93648. It seems that the new kernel that fixes the issues did not make it into that build.

---

