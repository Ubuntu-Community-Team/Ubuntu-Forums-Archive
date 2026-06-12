---
title: "Need (beginners) help with partitioning"
date: 2006-08-13
forum: Desktop Environments
---

### Post by mrspoons on 2006-08-13
I've installed ubuntu on an 80gb drive which is now split up into the following :
60GB - sda1 - XP Partition (NTFS)
10GB - Ubuntu
1GB - SwapFile
9GB - sda4 -Shared Drive (FAT32)

I need to get more space onto the 10gb partition by removing some from the XP partition.
I've tried gparted on the Live disk but after knocking down the xp partition to 30gb it wont let me move the spare 30gb anywhere.

Does anyone have any step by step instructions for a novice to go through?

I've had a search and couldnt find anything that relates to how I have this drive set up?

cheers

---

### Post by lupine_nickt on 2006-08-13
I'm not an expert - not even close ;) - but AIUI, you can't 'move' the 30GB, as it relates to a physical area of the disc. You can't merge it with the Ubuntu partition because you can only expand/retract a partition from the end - after all, all the important data is at the beginning! 

So your best bet is to turn the 30GB of free space into a seperate partition, copy over your 10GB ubuntu partition to that, then (once you've verified it's working!) delete the old ubuntu partition, and expand the new one to cover the space in question.

Unfortunately, I've no idea how to use gparted.

xF,

...Nick

---

