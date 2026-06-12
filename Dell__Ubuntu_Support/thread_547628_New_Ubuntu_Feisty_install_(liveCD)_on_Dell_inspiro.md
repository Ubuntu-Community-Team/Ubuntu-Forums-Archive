---
title: "New Ubuntu Feisty install (liveCD) on Dell inspiron 6400"
date: 2007-09-10
forum: Dell  Ubuntu Support
---

### Post by Monkey_Tales on 2007-09-10
**I want to install Ubuntu Feisty (live CD) on my Dell Inspiron 6400**

The problem with my Dell is that it has standard 4 partitions installed with WindowsVista and there are no more partition allowed.

2 partitions are visible and 2 are hidden.
**visible partitions:** 1 partition is for windows vista OS(100GB) and 1 partition is for Recovery (10GB; 3,5 GB used and 6,5GB free)
**hidden partitions:** 1 partition is called Mediadirect (2GB; 1,26 used and 780MB free) and 1 partition is Dellutilities (80 MB; 8mb used, 72 mb free)

If i want to install Ubuntu feisty from the live CD, it needs 3 partitions:
1 x ext3 for root, 1 x ext3 for home directory and 1 x linux swap.

What windowspartition can i overwrite for 3 linux partitions? without losing inportant vista data? Can i make 3 linux partitions from 1 windows partition?

Is there anybody with a Dell 6400 with an answer?

---

### Post by jnorthr on 2007-09-10
That is a shame. Seems like Dell have already used up all the four primary partitions. To solve your problem you will need to create logical partitions by converting one of those primary partitions into what is essentially a 'link' partition that just points to the extended partitions. You can make as many of these extended paritions up to 63 as you need. Your second problem is that the vista partition has the real disk space of 100GB, and you are going to need 10GB-20GB for ubuntu. I can't see how you can do it. If you know what the dell utilities are, you might be able to copy them somewhere and toast that partition, that's where i'd start.

Another idea : buy a big usb key and install on that. There are other threads on this forum that explain how to do it. It may just be a little easier than re-inventing the wheel. 8-)

---

### Post by Mr..Yeti on 2007-09-16
About a month ago i bought the same laptop and installed ubuntu, with vista. This is what i did, leaving vista, mediadirect and the backup partition intact.

I shrunk the main vista partition, with vista's partion tool. 
It only would only me about 20GB of space, so first I disabled 'backup tool?' (you can enable the backup after partitioning.)

The vista tool should leave you with free space. I got about 40GB.

THEN you can load into ubuntu, and from the installer set your partions up to how you want them. It seemed to set it up as extended and it all works. Mine are 14GB for ubuntu, 25 for /home and a 1GB swap. both data partitions are ext3.

One extra step i took was to install grub on the the ubuntu partition, so that the still has the bootloader, then you can use "Easy BCD" from vista to add ubuntu's grub.

---

### Post by Matthew Wiebelhaus on 2007-09-16
If your thinking about getting tid of vista you should might as well delete the media direct partion because you cant use it with linuz

---

### Post by neptho on 2007-09-19
> **Matthew Wiebelhaus said:**
> If your thinking about getting tid of vista you should might as well delete the media direct partion because you cant use it with linuz

The media direct partition is a *standalone* partition with it's own *blergh* copy of Windows on it.  If you want to use the 'media direct' button (outside of X11), you won't want to kill it.

I have mine tied to Amarok.  ;)

---

