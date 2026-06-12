---
title: "Adding a swap partition to Lubunut 10.04"
date: 2011-01-19
forum: Desktop Environments
---

### Post by M_Mynaardt on 2011-01-19
Hi!

First off, I apologize for three attempted and failed attempts at posting here today.  I was trying to post my question from my laptop on wireless and everything in forums worked except submitting a thread.  I kept getting timed out every time I tried that.  Weird...

But I digress...

I have a live/persistent install of Lubuntu 10.04 on a USB-HDD.  It's a 320 GB portable hard drive; I've set aside 80 GB for Lubuntu and the rest is partitioned for data storage.

I was being very cautious that I didn't mess up the boot loader for this install, but wasn't paying attention to the fact that Lubuntu does _not_ have a swap partition.  I incorrectly assumed it was just part and parcel of selecting ext4 as the file system.

Can someone tell me if it's possible to add a swap partition to this live install of Lubuntu?  I'd like to be able to set aside, say 3-4 GB for the swap partition.  Without losing any data in the process, of course!

Thanks in advance!

---

### Post by LinUxaliVe on 2011-01-19
> **M_Mynaardt said:**
> Can someone tell me if it's possible to add a swap partition to this live install of Lubuntu?  I'd like to be able to set aside, say 3-4 GB for the swap partition. 

Yes, you can resize one of your partitions, and create a swap ***partition*** with that space.

Alternatively, you could create a swap ***file*** instead. There should be a program that creates swap files for you *(use Google)*.

If I'm not mistaken a few Linuxes will auto-load any swap partitions/files automatically if they are detected. Though you can specify the swap partition in 'fstab' if necessary.

---

### Post by M_Mynaardt on 2011-01-19
> **LinUxaliVe said:**
> Yes, you can resize one of your partitions, and create a swap ***partition*** with that space.

Alternatively, you could create a swap ***file*** instead. There should be a program that creates swap files for you *(use Google)*.

If I'm not mistaken a few Linuxes will auto-load any swap partitions/files automatically if they are detected. Though you can specify the swap partition in 'fstab' if necessary.

I check those out, then, thanks!

---

