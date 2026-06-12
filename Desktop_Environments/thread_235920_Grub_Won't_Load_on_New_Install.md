---
title: "Grub Won't Load on New Install"
date: 2006-08-13
forum: Desktop Environments
---

### Post by marcinb on 2006-08-13
As you've probably guessed form the title, somehow grub is acting up.  The installation of Ubuntu appeared to go through without a hitch, but now on boot up I get a blinking cursor instead of grub, and as such, Ubuntu won't load off of the hard disk.  Now, I've got two hard drives in there currently (master on IDE1 and slave on IDE2, it was easier to put them in that way due to the layout of the computer), but made sure that Ubuntu installed on hda and that the computer tries to boot from the correct disk.  I've tried reinstalling from a different CD, swapping the install hard drive (had an extra lying around), disconnecting the second internal hard drive, and yelling at the computer loudly, but all to no avail.

Anybody have any ideas?  I'm not too well versed with grub, which is why I'm asking.

---

### Post by zxee on 2006-08-14
From the live cd you can try the command sudo grub-install and see if that does what you need or not. If there are messages or errors post them here.
Your hardware set up does seem a little odd. Are you saying that each of your two drives is on a different ide channel? What are they paired with then-optical drives?

---

### Post by marcinb on 2006-08-14
Not by that computer right this second, but I can answer this.

> **zxee said:**
>  Are you saying that each of your two drives is on a different ide channel? What are they paired with then-optical drives?

You're correct.  On the primary IDE channel I only have one hard disk (done so that I can easily install a second hard drive in the near future).  On the secondary IDE channel, I've got an optical drive and another hard drive, the BIOS claims that the optical drive is the master and the hard drive is the slave.  I just set the jumpers to cable select as I normally do (usually works just fine) and let the computer do the rest of the work.  This set up was done so because it was physically easier to put the hard drives in the machine that way... the box has a weird internal layout.

---

