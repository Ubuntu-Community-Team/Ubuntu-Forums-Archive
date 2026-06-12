---
title: "a different black screen problem (seems ubuntu mount is corrupted)"
date: 2009-04-30
forum: General Help
---

### Post by 21:27 on 2009-04-30
I upgraded to Jaunty a couple of days ago without any problems.
Today I woke up and checked my laptop(i don't turn it off most of the time) and there was something wrong with it. I guess pulse audio crashed again or something, so I restarted. Now when I select a kernel in GRUB, it just shows a black screen with a flashing underscore. Does not go past that. I burned a jaunty install CD and tryed to see what is the problem, but I can not mount my partition from there. It says something about wrong fs type, bad option, bad superblock and some more I don't remember right now. 
I got 64 bit Ubuntu.
Is there anything I can do?

---

### Post by cariboo on 2009-04-30
Boot from the LiveCD and run fsck on the hard drive in your laptop, When running fsck the drive should not be mounted.

Open an Applcations-->Accessories-->Terminal and type:

```
sudo fsck -a /dev/sda1
```

substitute your drive for the one in the example above.

---

### Post by 21:27 on 2009-05-01
Big thanks, it worked.

---

