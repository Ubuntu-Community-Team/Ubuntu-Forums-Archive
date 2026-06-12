---
title: "puppy files won't get outta my flash drive"
date: 2009-06-07
forum: General Help
---

### Post by Chevy86 on 2009-06-07
i bought a flash drive a few days ago and tryed putting puppy on it with puppy universal installer, it failed to boot so i tryed formatting it with gparted. it will format to any filesys i want it to, but the puppy files are still there and it wont let me delete them or add any other files. how do i fix this? i am running jaunty.

---

### Post by Old_Grey_Wolf on 2009-06-07
Was the flash drive unmounted before you tried to format it?

---

### Post by Chevy86 on 2009-06-07
not sure, i just followed the prompts for the installer but i think it was mounted b4 that

---

### Post by Chevy86 on 2009-06-07
oh sry i read that wrong, again not sure, should it be muonted or unmounted when i try to format?

---

### Post by Old_Grey_Wolf on 2009-06-07
It should be unmounted before you format it.

---

### Post by xxKillBillxx on 2009-06-07
Unmount the disk and then using Gparted, delete all of the partitions that are on the disk. Then just create a new partition that fills up the entire disk and format it to whatever filesystem that you want.

---

