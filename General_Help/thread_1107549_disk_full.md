---
title: "disk full?"
date: 2009-03-26
forum: General Help
---

### Post by freonchill on 2009-03-26
please forgive me if this is in the wrong location or has been discussed before, i could not find what i was looking for.

currently:

df

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             56094620  46937524   6330064  89% /
~6.14gb free

disk usage analyser (installed by default with ubuntu 8.10)
/dev/sda6
53.5gb / 44.8gb used / 8.7gb free

gparted
/dev/sda6
53.92gb / 45.19gb uses / 8.73gb free

before:
when my drive got full, it said "error saying cant write to disk, full"

checked 'disk usage analyser' and it says i had 4gb free
lets assume that it showing 4gb = 2gb df

why do the different programs report different free space?
why wont it write to the final 2gb?
whats going on?

everything is on a 60gb hd (i know the 60gb @ 1000 != 1024)
the drive is split up into two partitions
/ 55gb
swap 2gb

thanks,

---

### Post by x33a on 2009-03-26
might be due to reserved space, if you are using ext3.

[http://wiki.archlinux.org/index.php/Ext3_Filesystem_Tips#Reclaim_Reserved_Filesystem_Space](http://wiki.archlinux.org/index.php/Ext3_Filesystem_Tips#Reclaim_Reserved_Filesystem_Space)

you can reclaim that space with tune2fs.

---

### Post by freonchill on 2009-03-27
thanks,

that would make sense
53.5 * .05 = 2.67gb

is there a way to reduce that to 1%?

is there a reason that df & gparted are showing different remaining? (as when i got to about 4gb free gparted, would have been about 2gb df, even after taking into account for the ±2.5gb reserved, if gparted is correct, that leaves 1.4gb un-accounted for)

---

### Post by x33a on 2009-03-27
from the article
> tune2fs -m 1 /dev/sdXYas for the second question, i don't have any idea why they are showing different sizes.

---

### Post by freonchill on 2009-03-27
> Now to change your reserved space to 1% of the drive, which is fair for non-root filesystems.

so would that be **bad** since that is my "/" ?

repeat other question if anyone knows that answer...

---

### Post by x33a on 2009-03-27
i didn't notice you were trying this on root. i wouldn't suggest messing around with root partition.

to reclaim some space try:
```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

```

---

### Post by Slim Odds on 2009-03-27
> **freonchill said:**
> so would that be **bad** since that is my "/" ?

repeat other question if anyone knows that answer...

Since drives are so much larger these days, 1% is plenty. Also, if you feel comfortable booting a Live CD to fix disk full problems, then 0% is fine too.

---

### Post by freonchill on 2009-03-27
thanks guys,


(continuing question)
is there a reason that df & gparted are showing different remaining?

which is more accurate?

---

### Post by lensman3 on 2009-03-27
You can always write to the reserved portion of the disk as "super-user" or "root".  The OS reserves that part for its own (eventual) use, like making sure that new files are contiguous.   

You can never release (or increase) I-node space though.  That is setup when "mkfs" is run during format.

---

### Post by Slim Odds on 2009-03-27
> **lensman3 said:**
> You can always write to the reserved portion of the disk as "super-user" or "root".  The OS reserves that part for its own (eventual) use, like making sure that new files are contiguous.

The reserved space is established when the partition is formatted. This is usually done during the installation (not so much my the "OS", but by the install script).

The problem is that Ubuntu still defaults to 5% for all partitions. With the big drives and large partitions, this tends to be a LOT of space. Also, the only partition where it's really needed is /

It's especially painful every time I see people with a HUGE /home partition wasting 5% of that space for nothing.

---

### Post by freonchill on 2009-03-28
thanks guys,

i was able to change it to 1% which should get the "reserved" part down to 535mb (much better than the 2.6gb)

(continuing question)
is there a reason that df & gparted are showing different remaining?

which is more accurate?

---

### Post by freonchill on 2009-03-29
hrm, wierd, it posted the same thing again?

---

### Post by x33a on 2009-03-29
i suggest you make a new thread on this df, gparted issue.

---

