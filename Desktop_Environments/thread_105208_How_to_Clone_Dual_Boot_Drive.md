---
title: "How to: Clone Dual Boot Drive?"
date: 2005-12-17
forum: Desktop Environments
---

### Post by urusaiyatsu on 2005-12-17
Hello,

I have to replace my main drive which has Win XP Pro and Breezy on as a dual boot set up. The partitions are the usual:

WinXP - NTFS
Ubuntu
Linux Swap
Win-Linux Swap - FAT32

What's the best way to clone the existing drive, which is 60G, to a new 120G drive I have installed? 

I tried using Ghost and Partition Magic in Win and they both wouldn't let me do it.

Can someone give me a clue? 

Thanks.

---

### Post by cwaldbieser on 2005-12-17
[QUOTE=urusaiyatsu]Hello,

I have to replace my main drive which has Win XP Pro and Breezy on as a dual boot set up. The partitions are the usual:

WinXP - NTFS
Ubuntu
Linux Swap
Win-Linux Swap - FAT32

What's the best way to clone the existing drive, which is 60G, to a new 120G drive I have installed? 

I tried using Ghost and Partition Magic in Win and they both wouldn't let me do it.

Can someone give me a clue? 

Thanks.[/QUOTE]

Not sure about cloning the NTFS partition, but you could probably copy the entire Ubuntu partition with the "dd" command.  It would probably be best to do this from something like a LiveCD with the partition(s) you are going to copy mounted read-only.

---

