---
title: "Moving Linux Swap Partition?"
date: 2006-06-27
forum: Desktop Environments
---

### Post by magii on 2006-06-27
I need a tech check :) .  I want to delete a fat32 partition and add it to my main ubuntu partition.  Between the 2 partitions lies the swap partition.  My fdisk display looks like this:

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1824    14651248+   7  HPFS/NTFS
/dev/hda2            5993        9733    30049582+   5  Extended
/dev/hda3            1825        5992    33479460   83  Linux
/dev/hda5            6087        9733    29294527+   b  W95 FAT32
/dev/hda6            5993        6085      746959+  82  Linux swap / Solaris

What I'm thinking of doing is killing the fat32 and swap partitions, increasing the ubuntu partition and then recreating the swap partition.  This should result in the same device names being used.  

Being a newbie to the world of linux I was hoping someone could give me a warm and fuzzy on this prior to destroying my system :rolleyes: 

Thanks to the wonderful world of Ubuntu users I no longer feel like I'm doing this ](*,)

---

### Post by Ramses de Norre on 2006-06-27
The fat and swap are in an extended partition, you'll need to delete the swap and fat, shrink the extended to the size of the swap and create the swap inside it again.

Now the main problem is that you can't move ext3.. So you'll need to backup the Linux partition (if you want to do this: DON'T use cp!! Use find, I'll give you a suitable command if you want) remove the ext3 and recreate a bigger one. Then set your data in the new partition.

---

### Post by magii on 2006-06-27
[QUOTE=Ramses de Norre]Now the main problem is that you can't move ext3.. So you'll need to backup the Linux partition (if you want to do this: DON'T use cp!! Use find, I'll give you a suitable command if you want) remove the ext3 and recreate a bigger one. Then set your data in the new partition.[/QUOTE]

I shouldn't have to move the ext3???  I want to leave the beginning where it is and just move the end to encompass the free space.  Am I missing something?

When I'm done I want to have a small 15 gb windows system and a large 60 gb for ubuntu with the swap at the end of everything.

Also just for my education... Why not use cp and what is find? (I fear my education is incomplete.)

---

