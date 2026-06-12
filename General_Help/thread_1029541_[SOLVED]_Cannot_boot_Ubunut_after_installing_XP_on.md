---
title: "[SOLVED] Cannot boot Ubunut after installing XP on different Partition"
date: 2009-01-03
forum: General Help
---

### Post by baju on 2009-01-03
Hi
This is my situation: I had 3 Partitions: one for Ubuntu, one for swap and one for my personal files.
I needed Windows XP for just one day and my Swap-Partition was too big anyway ( 40 GB ), so I resized it to 8 GB and created a new partition in the free space. On that free Partition I installed Xp. Since that day I didn't touch my Ubuntu Partition ( no need for bootmanager, I simply set boot-flag with a gparted-livecd. I will kill XP as soon as possible ). If I now try to boot ubuntu, my bios tells me "Error while loading operating system". The Partition isn't damaged ( I can access it with the ubuntu livecd ) and everything seems fine, just seems like XP crashed the boot-options. Any good ideas how to fix this?

---

### Post by blubaustin on 2009-01-03
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

reinstall grub see if that works.

---

### Post by baju on 2009-01-03
Thanks, worked.
I assumed, the solution would be fairly simple.

---

