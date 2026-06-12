---
title: "Kernel panic after edit partitions."
date: 2006-02-27
forum: Desktop Environments
---

### Post by savas on 2006-02-27
Hi friends. Using gparted, i removed a primary partition and create an extended partition and logical partitions in it. Before editing my partition table like below;

/dev/hda1 -> fat32(WinXP), primary
/dev/hda2 -> ext3 (Ubuntu), primary
/dev/hda3 -> ext3 (Backups), primary
/dev/hda4 -> swap, primary

After editing;

/dev/hda1 -> fat32(WinXP), primary
/dev/hda2 -> ext3 (Ubuntu), primary
/dev/hda3 -> swap, primary   /* As you see path for swap partition changed */
/dev/hda4 -> extended
/dev/hda5 -> fat32, logical
/dev/hda6 -> ext3, logical

My problem is linux is not booting anymore, It gives kernel panic when competer boot. Error message is;

Kernel panic - not syncing : I/O error reading memory image.

I have searched the forums but i could not find a solution about this stuation. I am not using raid. And i guess cause of this problem is swap partiton path change. But i boot from live cd and change /etc/fstab to true swap partition and it gives no effect. I know that linux can boot without swap. Is exist a way turn of swap partition without booting linux, in other words using live cd.  I thing if i can run swapoff command, computer will boot. Thanks for any help. Have a nice day.

---

### Post by wrtrdood on 2006-02-27
Hmm... moving the swap partition should not affect the initial boot that way.  Did you initialize the new swap partition?  Could be there's data in it causing the kernel to go ape.

To disable it you might try using fdisk to set the type to 83 and see if it helps.  Most of the time I've seen a panic at this point is when the kernel couldn't find the root partition.

Definitely odd...

---

### Post by savas on 2006-02-27
Thanks friend. I have done it. I add 'resume=/dev/hda3' kernel parameter to grub.conf. Now linux can boot. Thanks again.

---

