---
title: "Restored linux partition from Ghost, free space incorrect"
date: 2005-05-07
forum: Desktop Environments
---

### Post by Rehevkor on 2005-05-07
In order to give linux the bulk of my 40gb hard drive and make the windows partition much smaller, I made a Ghost image of the linux partition and deleted all of the partitions. I then reinstalled Windows XP on an 8gb NTFS partition and used Partition Magic to create a 30gb ext3 partition and a 1gb swap partition. Finally, I used Ghost to restore the linux image to the new, larger partition.

Following instructions from another thread, I used my Knoppix CD to reinstall Grub. I was able to boot from the Ubuntu partition without a hitch.

However, it still reports my free space as being 1.3gb, not ~25gb as it should be now. gparted shows all but 1.3gb of the 30gb ext3 partition as being in use, which obviously isn't right.

How can I correct this problem, and make all that extra space available again?

Thanks in advance :-P

---

### Post by jeremy on 2005-05-08
This may not work, but there is nothing to lose; Try to make, then restore an image of your linux partition using partimage (partimage is on your knoppix cd, run it in a root console).

---

### Post by Rehevkor on 2005-05-08
[QUOTE=jeremy]This may not work, but there is nothing to lose; Try to make, then restore an image of your linux partition using partimage (partimage is on your knoppix cd, run it in a root console).[/QUOTE]

I don't have enough free space to do that. Most of this HD is that partition.  I can't use a partimage server either, since this laptop is the only linux PC on my network.

Besides, it would probably just copy the same incorrect filesystem information into the image. I need to somehow force it to recalculate the free space for the partition.

---

### Post by Rehevkor on 2005-05-08
Qtparted in Knoppix shows the correct free and used space, but gparted in Ubuntu (booted off the partition itself) shows that most of the drive is used space. Is there any way I can make that space available in Ubuntu?

---

### Post by Rehevkor on 2005-05-08
Nevermind, I figured it out myself. I had to boot my Knoppix cd and run resize2fs to expand the filesystem from the Ghost image to fit the new partition size. Seems to be working fine, and the free space is right where it should be.

---

