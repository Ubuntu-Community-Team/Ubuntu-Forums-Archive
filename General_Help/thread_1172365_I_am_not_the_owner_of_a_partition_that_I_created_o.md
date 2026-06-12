---
title: "I am not the owner of a partition that I created on a storage card.  HUH"
date: 2009-05-28
forum: General Help
---

### Post by speedy1979 on 2009-05-28
Hi everyone.  I having difficulty coping files to the root of a partition I created on a 2GB SD card.

I created two partitions on my 2GB SD card using Gparted.  The first partition is FAT16 flagged as boot and the second partition is exFAT2 with no flags.  I can copy files to the FAT16 partition without difficulty.  However when I attempt to copy files to the exFAT2 partition I get an error message that says the following: "The folder "bin" cannot be copied because you do not have permissions to create it in the destination."  

I attempted to change the permissions of the exFAT2 partition which mounts as NEWVOLUME by right clicking on it and selecting properties then permissions.  But it says "You are not the owner, so you cannot change these permissions".   How can that be?  I created the partition myself and I am the sole account owner on this computer.  How could the computer tell me that I am not the owner?

Also there is a strange directory called lost and found. What the heck is that....is that like the recycling bin in windows?

Please help.

p.s.  Don't flame me for not searching.  I would; if only I knew what to search under.

---

### Post by coffeecat on 2009-05-28
> **speedy1979 said:**
> the second partition is exFAT2 with no flags.

I'd never heard of a filesystem called exFAT2 and I was scratching my head until I came to...

> **speedy1979 said:**
> Also there is a strange directory called lost and found.

.. and there was the clue. I guess you mean ext2, which is a non-journalled Linux filesystem. (ext3 is the journalled version.)

The reason you are not the owner (even though you paid for it :wink: ) is that ext2 supports Linux/Unix permissions, and the root of an ext2 filesystem is owned by the superuser, root. In fact the whole filesystem is owned by root, except that root can change the permissions for any folder or file so that it is owned by an ordinary user. You are in the world of Unix now, with a much more sophisticated, and much more secure, system of permissions. The good news is that if you are using the first created account in Ubuntu, you have access to superuser privileges. But we can come back to that.

But for an SD card, you might be better off using an old Microsoft Filesystem like FAT16/FAT32 anyway. What do you need to use the SD card for? Why not just reformat the second partition to FAT16 or FAT32?

---

### Post by mikewhatever on 2009-05-28
You can easily change the permissions and ownership of that partition by repeating what you tried, but with Nautilus file browser open with admin privileges.
Press alt+f2, type **gksudo nautilus**, enter your password. Now navigate to the fat32 partition and change the ownership to your username.

---

### Post by speedy1979 on 2009-05-28
> **coffeecat said:**
> I'd never heard of a filesystem called exFAT2 and I was scratching my head until I came to...



.. and there was the clue. I guess you mean ext2, which is a non-journalled Linux filesystem. (ext3 is the journalled version.)

The reason you are not the owner (even though you paid for it :wink: ) is that ext2 supports Linux/Unix permissions, and the root of an ext2 filesystem is owned by the superuser, root. In fact the whole filesystem is owned by root, except that root can change the permissions for any folder or file so that it is owned by an ordinary user. You are in the world of Unix now, with a much more sophisticated, and much more secure, system of permissions. The good news is that if you are using the first created account in Ubuntu, you have access to superuser privileges. But we can come back to that.

But for an SD card, you might be better off using an old Microsoft Filesystem like FAT16/FAT32 anyway. What do you need to use the SD card for? Why not just reformat the second partition to FAT16 or FAT32?

The reason I need the ext2 filesystem is because i'm trying to boot linux on my Ipaq 211.  According to the info posted here: [http://www.handhelds.org/moin/moin.cgi/HpIpaq214HowTo](http://www.handhelds.org/moin/moin.cgi/HpIpaq214HowTo)
I need an active FAT16 partition and a ext2 partition.

---

### Post by speedy1979 on 2009-05-28
> **mikewhatever said:**
> You can easily change the permissions and ownership of that partition by repeating what you tried, but with Nautilus file browser open with admin privileges.
Press alt+f2, type **gksudo nautilus**, enter your password. Now navigate to the fat32 partition and change the ownership to your username.

Thanks for the help.  I got it to work.  

Linux sure is different from windows.

---

