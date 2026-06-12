---
title: "File system woes"
date: 2007-02-12
forum: Desktop Environments
---

### Post by KAL9000 on 2007-02-12
Right, I am new to all this so please be patient.

I am having trouble getting my head around the basics of the Lunix file system.

My idea of it is.
Linux sees a physical disk as "hd" followed by a letter corresponding to the order in which it its attached. e.g. hda, hdb, hdc
Then the partitions are marked by a number in order of where the partition starts on the disk.
e.g. hda1, hda2, hdb1.
for use the partitions have to be "mounted" for the OS to read write to them. when this happens you choose a mount point. In windows this is your "drive letter" e.g. C:
In Linux the mount point can be anywhere, and appear as normal folders and the contents of which are on a separate drive from the rest.

Is this the basic why of it all or is there anything else I should know.

My problem is that I'm finding it difficult to remember where everything is. what folder is what and the like.
Is there an equivalent to "/program files" as a default installation.  
I know /[user] is basically "/my docs"

---

### Post by dcstar on 2007-02-12
> **KAL9000 said:**
> Right, I am new to all this so please be patient.

I am having trouble getting my head around the basics of the Lunix file system.

My idea of it is.
Linux sees a physical disk as "hd" followed by a letter corresponding to the order in which it its attached. e.g. hda, hdb, hdc
Then the partitions are marked by a number in order of where the partition starts on the disk.
e.g. hda1, hda2, hdb1.
for use the partitions have to be "mounted" for the OS to read write to them. when this happens you choose a mount point. In windows this is your "drive letter" e.g. C:
In Linux the mount point can be anywhere, and appear as normal folders and the contents of which are on a separate drive from the rest.

Is this the basic why of it all or is there anything else I should know.

My problem is that I'm finding it difficult to remember where everything is. what folder is what and the like.
Is there an equivalent to "/program files" as a default installation.  
I know /[user] is basically "/my docs"

Everything starts at the "/" (root), all of your mount points are somewhere under that, the Linux system expects certain directories to be in specific places, but essentially you can make your own mount points anywhere you like (as long as they don't conflict with vital system ones).

You don't "have" to remember much at all, you should be working in your own Home directory and your file structure there is basically what you make of it - including mount points to other drives etc.

---

### Post by KAL9000 on 2007-02-13
I think the problem ive had is that ive tried to use the WHOLE system...so everything i make is Root only :(.
I assume that if I make a dir in my home folder and work EVERYTHING out of that inc the mount points does that mean I have full right's and ownership of that file?

my problem I've encountered now if you read another of my posts is how to replace my Home folder root with a new partition. so i can get more space without just adding another dir inside it, but that seems it may be the easiest thing. 

After looking through it all a bit more I seem to understand better.  /home/[user] is (unless I need to solve a problem or run a program/config) where all my files and my "working area" should be.

---

### Post by Ptero-4 on 2007-02-14
KAL9000. Put your mount points in /media , in that way your disks will show up in your desktop and in your ¨Computer¨ folder in the ¨Places¨ menu. And as for your /home, do this. Go to /home, type:
```
cp -R kal9000 /mountpoint
``` where kal9000 is your home folder and /mountpoint is the mount point of the partition/disk you will use as /home, then copy any other home folder (if you have more than one user account in your system) to the /home partition/disk, then in the recovery mode delete the contents of your /home folder in the / partition/disk and add your /home partition/disk to your /etc/fstab file.

---

