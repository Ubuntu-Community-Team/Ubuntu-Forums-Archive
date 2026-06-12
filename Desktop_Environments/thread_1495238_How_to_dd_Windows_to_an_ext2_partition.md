---
title: "How to dd Windows to an ext2 partition"
date: 2010-05-27
forum: Desktop Environments
---

### Post by pato wlmc on 2010-05-27
[FONT=Comic Sans MS]Well, for reason that i'm not going to explain here, i TOTALLY ****ed up my windows bootmgr, and, in some way, the linux partition too. I'd like to format the windows partition, but as all my info stays intact I'd like to conserve it that way.

The only way I can think of, is to make a new ext2 partition on the same HDD y have windows ( I only have one HDD, so... ) and save the information there . 

Wich is the correct way to do so, without losing all my software and/or information??

Thanks!

Other details:

* Rright now, i don't have ubuntu installed on my pc ( I'm using a live cd ).
* I'm using ( or was ) win 7.
* The only partitions on my HDD is an ntfs ( 60 GB ) and an unallocated  ( 240 GB )[/FONT]

---

### Post by Kilz on 2010-05-28
The live cd should have gparted installed, its a nice and easy partition manager that doesnt do anything until you click apply. You will find it in System > Administration > gparted.
Just use some free space to create the partition. I would recommend using fat32 as the format, that way windows will see it.

---

### Post by WinRiddance on 2010-05-28
> **pato wlmc said:**
> [FONT=Comic Sans MS]The only way I can think of, is to make a new ext2 partition on the same HDD y have windows ( I only have one HDD, so... ) and save the information there . 

* Rright now, i don't have ubuntu installed on my pc ( I'm using a live cd ).
* I'm using ( or was ) win 7.
* The only partitions on my HDD is an ntfs ( 60 GB ) and an unallocated  ( 240 GB )[/FONT]
.
Well, even if you save everything onto another partition first, you realize of course that formatting your Win7 partition will wipe out the entire Win7 system with everything that's a part of Win7. Anyway, assuming that your Win7 OS is actually still intact ... just not usable at the moment ... and furthermore assuming that you'd really actually prefer to use Ubuntu while keeping Win7 as an option, I'd suggest the following:

1. As suggested above, use the LiveCD to try Ubuntu without installing.
2. Open Gparted in the LiveCD and then split your unallocated 240 GB into two partitions
    **A.** One 100 GB backup partition** B.** One 140 GB partition **C.** Both in ext4 file system
3. Backup your existing Ubuntu data, if any, onto the 100 GB partition.
4. Use restart with the LiveCD to exit Ubuntu and restart/boot the system back into the CD.
5. This time install a fresh copy of Ubuntu into the 140 GB partition

Best of luck.

---

### Post by Barafu Albino Cheetah on 2010-05-28
If I understand you right, you want to save a partition in most intact state possible?
dd if=/dev/sda5 of=~/backup.img bs=1024. 
Just make sure you have enought space. You can always mount the resulting file as if it is a hard drive partition.

---

### Post by pato wlmc on 2010-05-28
IT's done, i just did it the way i thought it would work, and well, it did so.

After saving my whole HDD i just installed the Win 7 again and passed the partition, but conserving the boot files, and it worked.

Anyway thanks for everything.

---

