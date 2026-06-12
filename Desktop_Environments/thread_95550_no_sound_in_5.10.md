---
title: "no sound in 5.10"
date: 2005-11-26
forum: Desktop Environments
---

### Post by mistergq on 2005-11-26
I am using a Gateway 4520 notebook that I purchased a year ago.  Today, I installed Ubuntu on my laptop.

According to Ubuntu, my sound device is an Intel 82801db-ch4.  I do not have any sound.  If I use the external volume control next (on the case), a little window pops up showing the voluming going up and down.  Since Gateway does not support linux on this laptop, does anyone have any advice on how to proceed.

Thanks.

---

### Post by syklitengutt on 2005-11-26
open terminal and type sudo fdisk -l
and post the results here.
If you go into the system-admin-hardisks and you can find the hd there select it and click browse.

If the sys etc isnt the exact nameing its because im on windows 98 right now.

---

### Post by mistergq on 2005-11-26
Here are my results

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4256    34186288+   7  HPFS/NTFS
/dev/hda2            4257        7168    23390640   83  Linux
/dev/hda3            7169        7296     1028160    5  Extended
/dev/hda5            7169        7296     1028128+  82  Linux swap / Solaris

---

### Post by RAV TUX on 2005-11-26
[http://ubuntuforums.org/showthread.php?t=79959:p](http://ubuntuforums.org/showthread.php?t=79959:p)

---

### Post by mistergq on 2005-11-27
yozef.  Thanks for the tip.  tried it, but it did not fix my problem.  Still no sound.

---

