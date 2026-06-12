---
title: "Partition getting wrong name?"
date: 2006-09-22
forum: Desktop Environments
---

### Post by hornett on 2006-09-22
I've suddenly lost my disk's name from the desktop. :(

It's worked fine for months and booting up today it's become "[0011]"! (pic attached)

It's set to "Shared" in Windows and mtools shows it correctly too...what can be the problem?

PS. Tried with Ubuntu and my own kernel.org kernels, with same problem.

Any help much appreciated!

Andy :confused:

---

### Post by Omnios on 2006-09-22
Usually the drive name that shows on the desktop and the computer window is the file name at the mount point.

---

### Post by hornett on 2006-09-24
> **Omnios said:**
> Usually the drive name that shows on the desktop and the computer window is the file name at the mount point.

I thought it used the real volume label for VFAT windows partitions, but anyway the mountpoint is /media/Shared so in any case it should still get the name "Shared".

:(

---

### Post by Omnios on 2006-09-24
Oh ya I noticed names worked wierd pertiaining on your ftab entry but this is the first time I have seen that kind of name show up.

---

