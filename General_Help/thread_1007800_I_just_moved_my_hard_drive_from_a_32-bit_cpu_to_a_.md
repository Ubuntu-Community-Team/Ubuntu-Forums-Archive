---
title: "I just moved my hard drive from a 32-bit cpu to a 64-bit...."
date: 2008-12-10
forum: General Help
---

### Post by diablo75 on 2008-12-10
I just finished doing an upgrade on my PC.  I used to have a Winfast motherboard with a 32-bit Athlon processor running at 2.0 Ghz.  I just replace the motherboard with an Abit NF-M2PV with an Athlon 2X 64-bit 5200 (I think each core is 2.8 Ghz).

I'm just happy to see that everything works and I didn't have to arm wrestle with anything to get my system running (short of the soundcard, but I have a [separate thread dedicated to that problem]("http://ubuntuforums.org/showthread.php?t=1007787")).

At the moment, I don't really notice much of a performance increase over my previous system.  I was wondering if this might be because I'm not using the 64bit version of Ubuntu, or if it's because it came from an install that sat on top of older hardware.

One of the other things I was wondering is... I have two different types of DDR2 in use right now.  One stick is PC2-6400 and the other is PC2-5200.  The reason I did this was... I bought two sticks of 6400 but one of the sticks was bad.  So I thought I might just shoot for the moon and use an older stick of 5200 I had lying around just to see if it would work.  And it appears to be working.  But because the speeds are mismatched, I was wondering if this might cause significant slow downs in performance.

---

### Post by sdennie on 2008-12-10
For most of your apps, the CPU and number of cores isn't a bottleneck after a certain point.  Upgrading the CPU can help many things but, it won't make every part of the system noticeably faster.  Faster disks (or moving to an SSD) can make a big difference and adding more memory can make a difference because the cache can grow larger (which helps hide disk latency).  The lack of speed increase is certainly *not* caused by 32bit/64bit but just that you are looking in the wrong places for your speed increase.  As for your RAM differences, I don't think that will cause problems but it's not something I have experience with.

---

### Post by cdtech on 2008-12-10
> this might be because I'm not using the 64bit version of Ubuntu
Thats correct. The 64bit kernel is set to run dual core as with the applications. I haven't tried to replace a 32 with a 64 yet so I'm not sure what effect it would have.

---

### Post by modmadmike on 2008-12-10
Well one of the coolest things about x86_64 is its ram support - up to 64terrabytes in linux vs- 3-4gb with x86 looks like x64 will stay for a long while (however that's what they said about 32bit when it came out and look at it now If that happens again then I cant wait :))
Oh I upgraded from Vista to Vista x64 once (I was using linux before xp came out so don't call me a noob) and it Literally upped the speed by 4 times. Right now im using a 4 core phenom so if i can see a performance increase on that then you defiantly should :).

---

### Post by modmadmike on 2008-12-10
I cant Wait till 1 petabyte HDD's lol

---

