---
title: "RAID. Ubuntu. Questions."
date: 2009-06-01
forum: General Help
---

### Post by Roasted on 2009-06-01
I was considering on popping a pair of 250gb SATA drives in a spare HP desktop I have sitting around (1gb RAM, Pentium 4 processor) and using it as a samba storage server. Currently my main desktop does this (it houses a total of 4 drives, 2 for me, and the pair of 250s I spoke about above). I was considering on setting up RAID on this machine, though.

Thing is, I've had my nose in technology for quite a while yet I've never set up a RAID array. If I'd get this going, I'd use RAID 1 - mirroring. How would you do this with Ubuntu? Is this something to be done at BIOS level? How does Ubuntu play with software RAID? Are there any free options to get this job done?

If all else fails, I'll just make an rsync script and crontab it to run 4 times a day, which is currently how I have it set up on my main desktop as is. But, like I said, I'd like to learn this and play around with it while I have an opportunity.

---

### Post by munky99999 on 2009-06-01
[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)

Though honestly. Software Raid is often so like anti-performance. On top of that... basically all your "hardware raids" arent anything of the sort.

In my opinion you should avoid raid like the plague; especially as it sounds like you want to do it for the lulz.

Honestly backing up data is fairly easy. So unless you really need to avoid the human-factor; you should consider doing it the good ole fashion way instead of raid.

Now exception being obviously. Business or similar. You want raid, you want network syncing, you want ubuntu 1, and you want the olefashion copypasta.

In which case. There you go :) very first link provides proper links to methods.

---

### Post by albinootje on 2009-06-01
> **Roasted said:**
>  But, like I said, I'd like to learn this and play around with it while I have an opportunity.

If you want to play around, try the software RAID :
[http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1](http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1)
[http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch)

---

