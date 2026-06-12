---
title: "partition question"
date: 2009-04-23
forum: General Help
---

### Post by unitedwefall on 2009-04-23
Hi

I've been using ubuntu desktop for a few months and i love it (although i'm still dual booting with vista, and want to stay that way). Now 9.04 is out i want to get rid of 8.10 and use that instead. I just want to format my 8.10 partition and start again but im not really sure how, on the partitioner i guess you choose the custom bit but im really crap and i have no idea how to do it.

Thanks

x

fake edit: i know i could upgrade from 8.10, but if i did that, would it give me the option to completely format a partition?

---

### Post by unitedwefall on 2009-04-23
bump, sorry i suck at this

---

### Post by dabl on 2009-04-23
OK, high-level (that's where you have to start):

1. Boot a Live CD that has either GParted or Parted Magic on it.  Suggested sources for a downloaded ISO that you can burn:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

[http://partedmagic.com/](http://partedmagic.com/)

2. Assuming you are satisfied with the existing partition sizes on your hard drive, use the partitioning tool first to DELETE the partition, and then to make a NEW partition there, of the same size, and with your desired filesystem type.  Click "Apply" and it will reformat that partition.

3. Now you can boot your *buntu Live CD or Alternate Install CD, and when you get to the partitioning phase, choose "manual" and then choose the partition that is empty that you just re-formatted.  Set the mount point to "/" and you're ready to proceed.


OH YEAH -- don't do anything before you've backed up your data!  ;)

---

### Post by unitedwefall on 2009-04-23
OK cool, what filesystem type should i use?

---

### Post by dabl on 2009-04-23
> **unitedwefall said:**
> OK cool, what filesystem type should i use?

Ext3 to be very safe.  Ext4 to be bold and adventuresome.

:lolflag:


Seriously, I installed on ext4 three weeks ago, and have seen no signs of any issues with it.  The fscks are way faster than ext3.

---

