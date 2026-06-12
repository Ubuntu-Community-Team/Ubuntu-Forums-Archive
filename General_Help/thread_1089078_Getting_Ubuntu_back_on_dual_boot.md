---
title: "Getting Ubuntu back on dual boot"
date: 2009-03-06
forum: General Help
---

### Post by D-Dan on 2009-03-06
OK - I've done some searching and I can't find an answer that works for this. If it's there and I've missed it, I apologise, and ask that you point me in the right direction.

Until last week, I had dual boot XP32 and Ubuntu64. I bought a new HD, and decided to retry Vista64. Vista is installed on a partition on the new HD (with a huge amount of unallocated space on it), my original XP drive (with Ubuntu dual booting) is on HD No 2, and HD No 3 is my general data drive.

Each drive is partitioned to suit my needs.

Having got Vista installed, I now want to restore my dual boot with Ubuntu (I'm not too concerned with XP, though it'd be nice to keep it available).

now, I've been able (pre vista) to restore grub if I had to re-install XP, but the same process will not play ball anymore. In a nutshell, I booted from a liveCD, did sudo grub - and attempted to find stage1. Whilst this has always worked before, now it no longer finds it.

So, how do I get grub and my Ubuntu install back?

I've tried using Vista's boot manager and easyBCD - which doesn't work (though I'd prefer Grub anyway). I'm happy to ghost Ubuntu using DriveimageXML if it helps, but my goal is to get Ubuntu onto the old XP drive - repartiotning as necessary once I can boot.

For info, I'm using 64 bit versions of both Vista and Ubuntu, SATA drives on AMD X2 6200. grub was originally installed on what is now HD2.

Please let me know if you need more info. I'm very proficient with Windows, and a knowledgeable amatuer with Linux.

TIA

---

### Post by linuxisevolution on 2009-03-06
> **D-Dan said:**
> OK - I've done some searching and I can't find an answer that works for this. If it's there and I've missed it, I apologise, and ask that you point me in the right direction.

Until last week, I had dual boot XP32 and Ubuntu64. I bought a new HD, and decided to retry Vista64. Vista is installed on a partition on the new HD (with a huge amount of unallocated space on it), my original XP drive (with Ubuntu dual booting) is on HD No 2, and HD No 3 is my general data drive.

Each drive is partitioned to suit my needs.

Having got Vista installed, I now want to restore my dual boot with Ubuntu (I'm not too concerned with XP, though it'd be nice to keep it available).

now, I've been able (pre vista) to restore grub if I had to re-install XP, but the same process will not play ball anymore. In a nutshell, I booted from a liveCD, did sudo grub - and attempted to find stage1. Whilst this has always worked before, now it no longer finds it.

So, how do I get grub and my Ubuntu install back?

I've tried using Vista's boot manager and easyBCD - which doesn't work (though I'd prefer Grub anyway). I'm happy to ghost Ubuntu using DriveimageXML if it helps, but my goal is to get Ubuntu onto the old XP drive - repartiotning as necessary once I can boot.

For info, I'm using 64 bit versions of both Vista and Ubuntu, SATA drives on AMD X2 6200.

Please let me know if you need more info. I'm very proficient with Windows, and a knowledgeable amatuer with Linux.

TIA

Well, boot a live cd on Ubuntu, open a terminal and type sudo grub. Then type find /boot/grub/menu.lst . Then type setup (hdX,X) replacing X with what "find /boot/grub/menu.lst" gives you. Then type setup hd0. That should install grub with all your operating systems. you can edit the /boot/grub/menu.lst file to add operating systems to the boot menu.

---

### Post by neanderthalman on 2009-03-06
can you post the output of 

```
sudo fdisk -l
```

I think you can manually point grub to the right partition that contains /boot/grub/stage1 based on the above information, rather than using the "find" command.

---

### Post by D-Dan on 2009-03-06
Wow - that was quick. Since I may decide to re-use the old boot partition, I'll try this approach first. I'll let you know how I get on (in 10 minutes or so)

---

### Post by ponyexpress on 2009-03-06
Sounds like you need to set your bios boot order to boot from your second drive.

---

### Post by D-Dan on 2009-03-06
Thanks for the replies. Unfortunately, grub doesn't find the previous install, and I'd rather not change the boot drive since I'm planning on reformatting it.

I'm scared to death of trashing Vista now it's working (you have no idea the hoops I have jumped through) so I may take the unspoken option which is re-install Ubuntu :(

---

