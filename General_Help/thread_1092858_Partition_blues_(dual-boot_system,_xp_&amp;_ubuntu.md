---
title: "Partition blues (dual-boot system, xp &amp; ubuntu)"
date: 2009-03-10
forum: General Help
---

### Post by callie510 on 2009-03-10
Hey yall, I am so frustrated right now and would appreciate any help!!

I have been happily running a dual-boot system for a while now with a partition setup as follows:
1) 80gb ntfs - Windows Vista
2) 60gb ext3 - Ubuntu /home
3) 8gb ext3 - Ubuntu root
4) 3gb swap

So I'm 'upgrading' to XP, and while I'm at it I want to shrink that first partition. I'm hoping to end up here: 
1) 20gb ntfs - Windows XP
2) 120gb ext3 - Ubuntu home
3) Ubuntu root
4) swap

Here's my problem. Gparted doesn't see my partitions! I'm sitting here in Ubuntu, happily working with at least 3 mounted partitions, and Gparted says my entire drive is "unpartitioned space." I have booted into the Ubuntu Live CD, and Gparted says precisely the same thing there. I have tried to boot the Gparted cd itself, and after 15 minutes of errors I gave up on ever getting it to load.

Can someone please help me? I know my drive is OK, and I've checked my fstab and everything looks just fine. What should I use to delete, create, and expand my partitions if Gparted won't work?

Thanks!

edit: oh, I'm running Intrepid fyi

edit2: I'm pretty sure I can use fdisk to do this. Can I?

---

### Post by meierfra. on 2009-03-10
Probably the partition table needs  some minor fixing. Post the output of

```

sudo parted /dev/sda print
sudo fdisk -lu
sudo sfdisk -d
```

---

