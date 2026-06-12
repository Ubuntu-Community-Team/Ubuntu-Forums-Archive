---
title: "Firewire Drive question"
date: 2006-08-11
forum: Desktop Environments
---

### Post by salsaseb on 2006-08-11
I've had Ubuntu 606 on my desktop pretty much since it was released in June, and I have been extremely happy with it.
However (and I know I am going to get flamed for this) because of the nature of my usage of the Desktop PC, I have decided to revert to Windows XP on that machine, and am trying to figure out how to transfer my drives back to NTFS.

When I first installed Ubuntu, I had enough spare room on my hard drives to shuffle data back an forth as I formatted partitions from NTFS to ext3. Now, however, I no longer have enough room (data accumulation) to do the same thing. Furthermore, it's easier from NTFS->Linux, since NTFS write support is easy to configure on Ubuntu.

I have decided to purchase a large Firewire drive, onto which I would transfer the entirety of my files, to then get them once the box is running XP.

As I have not yet experimented with Firewire on Linux, I am not sure how well my plan will work, and I have several questions:

1- Firewire drives: will it be fairly easy to get them to be recognized by Ubuntu?
2- Will Ubuntu give me trouble in getting RW permissions on the drive?
3- Will Ubuntu want to format the drive into a Linux-friendly filesystem?
4- Will XP be able to recognize and read from the drive after all my files are transfered?
5- If (as I sort of expect) I do need to format the drive, I suppose I would be advised to use FAT32. Will I have any trouble with long file names, or names containing arcane characters (accents, Chinese words...) ?

Obviously, these are fairly basic questions. Although I do work in computers, my usage of Linux has so far only been to play with it at home, and my experience in Linux is quite limited.

I would finish my little letter by saying that Ubuntu is by no means losing a user. I am still using Ubuntu (dual-booting XP) on my Compaq laptop (no other distro comes even close in terms of out-of-the-box hardware support) and am planning on buying another PC to be an Ubuntu file server for my home network.

Thank you for your help and advice.

---

### Post by orasis on 2006-08-11
> **salsaseb said:**
> I've had Ubuntu 606 on my desktop pretty much since it was released in June, and I have been extremely happy with it.
However (and I know I am going to get flamed for this) because of the nature of my usage of the Desktop PC, I have decided to revert to Windows XP on that machine, and am trying to figure out how to transfer my drives back to NTFS.

When I first installed Ubuntu, I had enough spare room on my hard drives to shuffle data back an forth as I formatted partitions from NTFS to ext3. Now, however, I no longer have enough room (data accumulation) to do the same thing. Furthermore, it's easier from NTFS->Linux, since NTFS write support is easy to configure on Ubuntu.

I have decided to purchase a large Firewire drive, onto which I would transfer the entirety of my files, to then get them once the box is running XP.

As I have not yet experimented with Firewire on Linux, I am not sure how well my plan will work, and I have several questions:

1- Firewire drives: will it be fairly easy to get them to be recognized by Ubuntu?
2- Will Ubuntu give me trouble in getting RW permissions on the drive?
3- Will Ubuntu want to format the drive into a Linux-friendly filesystem?
4- Will XP be able to recognize and read from the drive after all my files are transfered?
5- If (as I sort of expect) I do need to format the drive, I suppose I would be advised to use FAT32. Will I have any trouble with long file names, or names containing arcane characters (accents, Chinese words...) ?

Obviously, these are fairly basic questions. Although I do work in computers, my usage of Linux has so far only been to play with it at home, and my experience in Linux is quite limited.

I would finish my little letter by saying that Ubuntu is by no means losing a user. I am still using Ubuntu (dual-booting XP) on my Compaq laptop (no other distro comes even close in terms of out-of-the-box hardware support) and am planning on buying another PC to be an Ubuntu file server for my home network.

Thank you for your help and advice.

1. - Yes if you have the proper software and hardware drives. 
2. - Not if you sudo. 
3. - It will most likely want to, but you can access a windows file system also (with some extra tweaking/mounting)
4. - You will have no problems with long filenames - however as for Chinese you will need to have a language pack installed in Ubuntu. 

[http://www.fwdepot.com/firewiredepot-forum/viewtopic.php?t=6&highlight=&](http://www.fwdepot.com/firewiredepot-forum/viewtopic.php?t=6&highlight=&)

That should help point you in the right direction towards your first steps.

---

