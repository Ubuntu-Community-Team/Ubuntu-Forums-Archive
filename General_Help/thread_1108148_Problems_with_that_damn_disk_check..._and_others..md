---
title: "Problems with that damn disk check... and others."
date: 2009-03-27
forum: General Help
---

### Post by Drayakir on 2009-03-27
Hi. First post and all that, but I have a question regarding Intrepid Ibex kubuntu.

I installed it on a friend's computer, and after the installation finished it worked fine. I installed firefox, pidgin, and the sun-java stuff, and that's it. Later on, I get a phonecall from my friend's mother who says that the computer was improperly shut down, and it freezes at 5% checking the drives. I did them in sda2 format. 

Then, when I did the memtest 86+ it sure gave me a lot of errors while it was checking. I haven't been to her place yet, but when I was leaving it had like... 1000 fails to 0 passes. Anyway. 

When I tried the recovery mode, it gave me a kernel panic- not syncing: Fatal exception in interrupt. Then, every time I'd try it, it would give me one of these reasons: mempool_free or blkdev_get_block.

So. Is there a chance this might be a hardware problem? Or is there something I can do, other than reinstalling it. Any help would be appreciated.

---

### Post by cariboo on 2009-03-27
Memtest checks ram for errors, if you are getting a lot of errors, I would suspect bad ram.

Jim

---

### Post by HermanAB on 2009-03-27
What file system did you use?  You should use one of ext3, jfs or xfs.  Anything else is best avoided.

It sounds like you need to re-install and your friend may want to invest in a UPS.

---

### Post by Kevbert on 2009-03-27
That suggests that you've got badly seated RAM. It may just be a case of removing and refitting the memory module.

---

