---
title: "does FSck check ALL partitions every 30 mounts?"
date: 2009-03-25
forum: Desktop Environments
---

### Post by mister_p_1998 on 2009-03-25
Just replaced a drive, and had to fsck it before it would clone, and my HDA3 said it hadn't been checked for 79 mounts?? Are all partitions checked automatically? or do I have to put it in manually for all additional partitions after root?

Steve

---

### Post by vanadium on 2009-03-25
Wether the partition is checked or not is determined by the setting in /etc/fstab (last digit on the line for the drive). Drives not in /etc/fstab such as external USB drives are never automatically checked.

---

### Post by mister_p_1998 on 2009-03-25
They ARE in FStab...
what Im saying is... are all the drives in FStab checked every 30 mounts?

Steve

---

### Post by vanadium on 2009-03-25
Whether the partition is checked or not is determined by the setting in /etc/fstab (last digit on the line for the drive).

---

### Post by kanikilu on 2009-03-25
> **mister_p_1998 said:**
> They ARE in FStab...
what Im saying is... are all the drives in FStab checked every 30 mounts?

Steve

Unless otherwise specified, yes, I believe that's the default. You can change that with tune2fs, though.

More information:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[http://ubuntu.wordpress.com/?s=tune2fs](http://ubuntu.wordpress.com/?s=tune2fs)

---

### Post by vanadium on 2009-03-25
I guess some more information will be needed.

Whether the partition is checked or not is determined by the setting in /etc/fstab (last digit on the line for the drive). If the last number reads "0", no checking is done. If it reads 1 or 2, checking is done (first priority, second priority). The system drive typically has one, meaning it is checked first. Other drives with 2 are checked simultaneously after these with "1" are finished.

For ext3, the check is a fast one. Every once in a while (by default in Ubuntu every 30 days or every 30 mounts, whichever comes first), a torough check is performed. The settings that dictate when full checking occurs is stored per partition and indeed can be changed using the tune2fs command.

---

### Post by mister_p_1998 on 2009-03-26
> **vanadium said:**
> I guess some more information will be needed.

Whether the partition is checked or not is determined by the setting in /etc/fstab (last digit on the line for the drive). If the last number reads "0", no checking is done. If it reads 1 or 2, checking is done (first priority, second priority). The system drive typically has one, meaning it is checked first. Other drives with 2 are checked simultaneously after these with "1" are finished.

For ext3, the check is a fast one. Every once in a while (by default in Ubuntu every 30 days or every 30 mounts, whichever comes first), a torough check is performed. The settings that dictate when full checking occurs is stored per partition and indeed can be changed using the tune2fs command.

THANKYOU!
that is the information I was trying to find out, it was only enabled on my first partition,I'll do it as soon as I get home, is there any way to set different check times for different partitions? eg, 30 for root, 50 for sda3,4,5 etc?

Steve

---

### Post by vanadium on 2009-03-26
> is there any way to set different check times for different partitions? eg, 30 for root, 50 for sda3,4,5 etc?

That is where you use tune2fs, e.g.

sudo tune2fs -c 50 -i 1m /dev/sda1

will set mount count to 50 and interval to 1 month.

---

