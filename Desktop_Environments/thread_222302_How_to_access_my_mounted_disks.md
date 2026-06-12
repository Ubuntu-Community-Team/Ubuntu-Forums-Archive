---
title: "How to access my mounted disks?"
date: 2006-07-24
forum: Desktop Environments
---

### Post by djgenesis on 2006-07-24
Hello all, i have installed the latest ubuntu and i have mounted my windows NTFS drives. The only problem is that i can't write on them. I only have read access. How do i change that?

---

### Post by reacocard on 2006-07-24
linux doesn't have good ntfs write support built-in, that's why it's read-only by default. search these forums for "ntfs 3g" and you'll find some stuff on getting write access.

---

### Post by x64Jimbo on 2006-07-24
NTFS write support is unstable and in BETA at the moment. Fortunately, a large breakthrough was made recently, in which NTFS write support was implemented nearly flawlessly. The Linux community has been abuzz ever since. The bad news is that the programmer whose work led to this breakthrough has gone on a month-long expedition, and as such is unavailable to contribute to the progress of his driver. 
The good news is that, due to the nature of this breakthrough and the rabid desire among so many Linux fans to have NTFS write support, it is likely that we will see a fully supported NTFS write driver in Ubuntu's repositories in a short while. Until then, the best things I can offer you are to have a FAT32 partition that Linux and Windows can write to, or an ext3 partition, which is also writeable by Linux, and even Windows if you get a special program for it. 
Patience will probably be the best bet here, as the new driver looks like it will outperform even the extended filesystems in Linux, and NTFS may become a staple in Linux mass storage. :)

---

### Post by djgenesis on 2006-07-24
Thanks for the swift response guys. I will convert one of my drives into FAT32. I should thank God that at least i have read access...

---

### Post by hellmet on 2006-07-26
u now have NTFS Read Write access now..
please check appropriate thread on HOWTO

---

### Post by x64Jimbo on 2006-07-27
It's not for everyone, and it's still in beta - not a good idea if you want to keep your Windows system intact. Use fat32 for now. No danger there.

---

### Post by djgenesis on 2006-07-27
I was always open to new ideas (and resulting catastrophes) and i think I might indeed be able to spare a 40Gb HDD of windows programs just to see if the beta works for me. 
Does anyone have the link for the how to ?

---

### Post by x64Jimbo on 2006-07-27
[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)

---

### Post by djgenesis on 2006-07-27
Tx J :)

---

