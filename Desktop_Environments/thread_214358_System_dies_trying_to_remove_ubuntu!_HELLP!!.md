---
title: "System dies trying to remove ubuntu! HELLP!!"
date: 2006-07-12
forum: Desktop Environments
---

### Post by anil_robo on 2006-07-12
Hi All
 
I am selling my Dell laptop to someone and he wants me to remove Ubuntu and keep windows XP only. I boot with a windows98 bootdisk and type fdisk /mbr to replace the master boot record. Done, no errors. I reboot system, and windows XP fails to start - stuck up just "before" the login screen.
 
I found a bootable disk with partition magic I made few years ago - booted with it, and ran partition magic. It says "Partition dismounted improperly".
 
What do I do to recover those partitions? Sorry I can't format them because there's valuable data in there!
 
HELLLLPPPP! :(

---

### Post by Tagmaster on 2006-07-12
Does it give you an autochk error before reeboting the system?

---

### Post by anil_robo on 2006-07-12
> **Tagmaster said:**
> Does it give you an autochk error before reeboting the system?
 
No, no errors whatsoever. The system simply halts just before the screen where it should have said "starting windows" or something like that...

---

### Post by Tagmaster on 2006-07-12
i dont know i got a similar problem once, it was because my win partition was set as the default boot in the MBR, but the partition was set as hidden, i fixed it using the ubuntu live cd and installing QTParted bacause Gparted was not able to change this

---

### Post by anil_robo on 2006-07-12
Thanks for assistance! Well, now I'm beginning to get some hints as to what went wrong!
 
First, I had installed windows xp in the first partition, but it appeared as drive f for some strange reason. I was expecting it to come as drive c, but it always comes up as drive f. Now that I've rewritten the boot record, this change must've done something bad, for example - causing windows to search for itself on drive f rather than drive c, but  drive f has now become drive c due to rewriting of master boot record.
 
Sounds strange, but windows xp is unable to detect where it lies!!!
 
Anyway, I think I'm not the first and last person to have encountered such a position, and here is what I'm doing right now:
 
I have deleted the linux partitions and formatted them as FAT. I am now installing windows xp on this fresh FAT partition, will boot in windows xp, and hopefully I'll see the lost partitions when it boots up. If it happens, I'll backup my data and then do a fresh install of xp before handing the laptop over to the buyer tomorrow.
 
If I'm unable to fix this in another six hours, I'll erase the entire HD and rewrite the partitions and reinstall XP for this person. I'll have to lose about 30 GB of mp3s I ripped from my and dad's huge CD collection, again! :(

---

