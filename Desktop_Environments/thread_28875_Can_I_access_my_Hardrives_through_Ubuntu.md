---
title: "Can I access my Hardrives through Ubuntu?"
date: 2005-04-22
forum: Desktop Environments
---

### Post by Goober on 2005-04-22
Hello,

I recently had my Windows decide to crap out on me.  My Main Boot Record got corrupted, and I can't access my Windows anymore.  I got hold of Ubuntu, though, so I am using that.

Now, my question is can I use Ubuntu to access my Hardrives (Both Primary and Secondary) to try and save some information that I want to, or to perhaps get Windows working?  I have heard that you can, but I have no idea how.  Could someone help me?

Mods - I wasn't sure where to put this.  I figured that this is the best place for this thread.  If not, my apologies.

I am running Ubuntu version 4.10, the Warty Warthog edition, I guess.  I have it installed on my Secondary Hardrive.

Thanks!  :)

---

### Post by nemin on 2005-04-22
[QUOTE=Goober]Hello,

I recently had my Windows decide to crap out on me.  My Main Boot Record got corrupted, and I can't access my Windows anymore.[/QUOTE]
I'd advise to boot with a windows bootfloppy and enter```
fdisk /fixmbr
``` That'll probably fix your mbr.
[QUOTE=Goober]
  I got hold of Ubuntu, though, so I am using that.

Now, my question is can I use Ubuntu to access my Hardrives (Both Primary and Secondary) to try and save some information that I want to, or to perhaps get Windows working?  I have heard that you can, but I have no idea how.  Could someone help me?[/QUOTE]
You can 'mount' your existing windows partions and read them with Ubuntu. I think you'll find this like useful:
[http://ubuntuguide.org/4.10/index.html#windows](http://ubuntuguide.org/4.10/index.html#windows)
Good luck.

---

### Post by Goober on 2005-04-22
Ok, I have successfully been able to Mount my Primary Hardrive, now what I need to do is to Mount my Secondary Drive.  Any suggestions on how to do that?

---

### Post by nigel on 2005-04-23
I think all you need to do is exactly what you did for the primary harddrive but use hdb instead of hda (assuming it is a seperate Harddrive) and of course have a diiferent name for the mount point, assuming it's fat 32 try below

sudo mkdir /media/bob

sudo mount /dev/hdb1 /media/bob -t vfat -o umask=000

---

### Post by Nu-Buntu on 2005-05-05
I have a related question. I have multiple partitions on my hard drives. How do I get a readout of what they are? For example, I know my NTFS primary XP installation is hda1, so it is mounted. I have 2 more NTFS partitions, plus a second HDD (hdb I assume) with multiple FAT32 partitions. How do I tell which is which so I can establish mount points?

---

### Post by Goober on 2005-05-05
That did not work Nigel.  I got the following: 

"mkdir: cannot create directory `/media/bob': File exist"

I think that that partition might have been formatted when I installed linux.  How would I find out if anything even exists on the partition?

---

### Post by nemin on 2005-05-06
[QUOTE=Nu-Buntu]I have a related question. I have multiple partitions on my hard drives. How do I get a readout of what they are? For example, I know my NTFS primary XP installation is hda1, so it is mounted. I have 2 more NTFS partitions, plus a second HDD (hdb I assume) with multiple FAT32 partitions. How do I tell which is which so I can establish mount points?[/QUOTE]
When you just want to see wich partitions are FAT32/NTFS etc, you can use parted. You can also simply mount every partition and have a look wich each is:)

---

### Post by nemin on 2005-05-06
[QUOTE=Goober]That did not work Nigel.  I got the following: 

"mkdir: cannot create directory `/media/bob': File exist"[/QUOTE]
Then just skip the mkdir step and directly enter```
sudo mount /dev/hdb1 /media/bob -t vfat -o umask=000
```
[QUOTE=Goober]
I think that that partition might have been formatted when I installed linux.  How would I find out if anything even exists on the partition?[/QUOTE]
With parted, you can see if the partition still exists. By mounting it, you can see what's on it...

---

### Post by Nu-Buntu on 2005-05-06
[QUOTE=nemin]When you just want to see wich partitions are FAT32/NTFS etc, you can use parted. You can also simply mount every partition and have a look wich each is:)[/QUOTE]
 nemin,

Thanks. I will try parted. The reason I want to see is so that I CAN mount them. I guess I don't know how to do that without finding what the partitions are. Parted sounds like it could be the solution.

Thanks for the help!

---

### Post by Goober on 2005-05-06
[QUOTE=nemin]Then just skip the mkdir step and directly enter```
sudo mount /dev/hdb1 /media/bob -t vfat -o umask=000
```

With parted, you can see if the partition still exists. By mounting it, you can see what's on it...[/QUOTE]

Hmm, when I enter that in to the Terminal, I get this:

"mount: /dev/hdb1 already mounted or /media/bob busy
mount: according to mtab, /dev/hdb1 is mounted on /"

Any suggestions for that?

---

### Post by nemin on 2005-05-06
[QUOTE=Goober]Hmm, when I enter that in to the Terminal, I get this:

"mount: /dev/hdb1 already mounted or /media/bob busy
mount: according to mtab, /dev/hdb1 is mounted on /"

Any suggestions for that?[/QUOTE]
It looks like you installed Ubuntu on that partition, so it's already mounted ;) I think you're willing to mount another partition. With parted you can see all partition on a harddisk.

---

### Post by Goober on 2005-05-06
Hmm, I think I discovered my problem.  Linux does not seem  to recognize that I partitioned the second Hardrive.  When  I installed Ubuntu (On my Secondary Hardrive) I gave Ubuntu a 4 Gig partition, and left the rest of it as a 150ish Gig partition.  Linux only recognizes the Linux partition, I guess.

I typed this in 

```
sudo fdisk -l
```

and that gave me

```
Disk /dev/hda: 41.1 GB, 41110142976 bytes
75 heads, 63 sectors/track, 16993 cylinders
Units = cylinders of 4725 * 512 = 2419200 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       16990    40138371    7  HPFS/NTFS

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1           19456       19929     3807405   83  Linux

```

So, on hdb, thre is a crapload of partitioned space with stuff on it, that I cannot access because Linux doesn't recognize the partition . . . blech, this is giving me a headache . . . any help anyone?

Thanks for your help this far.

---

### Post by nemin on 2005-05-07
[QUOTE=Goober]
[fdisk]

So, on hdb, thre is a crapload of partitioned space with stuff on it, that I cannot access because Linux doesn't recognize the partition . . . blech, this is giving me a headache . . . any help anyone?[/QUOTE]
I'm guess the problem is not linux isn't recognizing the partition, but I'm afraid the patitions are just gone. I hope I'm wrong...
You could try to re-create the partitions on the exact same location as they were to get your data back, since the data probably isn't deleted, just the partition's gone.

---

### Post by Goober on 2005-05-08
Ohhhh, I get it.  I partitioned a space for linux, but nothing for the rest of the crap on there.  Ok, thanks a lot.  I need to get a program to partition it, to Mount it, to attempt to salvage data.

Ok, thanks a lot.  I figured it was something like that.

---

