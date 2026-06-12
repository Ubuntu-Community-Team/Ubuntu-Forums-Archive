---
title: "GRUB Error 17"
date: 2009-01-04
forum: General Help
---

### Post by Jay money on 2009-01-04
Okay, today I realized that I had 10 Gigs of free space on my hard drive, so I decided to Make that into a FAT32 Partition so that I could have some swap space that could be used in Ubuntu and Windows. But, I did my partitioning in Windows. When I rebooted I got a GRUB error 17 and I've tried to find the answer, but to no avail. So, I'm at a loss of what to do. Please help me. I think that Windows Partitioning did something to my MBR though.

Fdisk -l
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11108    83976448+   7  HPFS/NTFS
/dev/sda2           11109       19045    59994742+  83  Linux
/dev/sda3           19045       20674    12313822+   5  Extended
/dev/sda5           19045       20407    10302358+   b  W95 FAT32
/dev/sda6           20408       20674     2008125   82  Linux swap / Solaris
```

---

### Post by tuxxy on 2009-01-04
You may just need to restore GRUB theres a good guide [here]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by Jay money on 2009-01-04
Oh Thank You, I can boot into Ubuntu after reinstalling GRUB, I was thinking that I might have to reinstall Ubuntu to get GRUB back. Thanks

---

