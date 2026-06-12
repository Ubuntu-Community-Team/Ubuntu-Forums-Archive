---
title: "mounted hard drive won't show up after reboot"
date: 2010-05-08
forum: Desktop Environments
---

### Post by Swiftjay on 2010-05-08
So I just got ubuntu installed for the first time, I tried mounting my hard drive to my desktop so i can have easy access to it, but when i restart ubuntu it always dissapears and i have to go to places then click on the hard drive again to mount it to my desktop. 

 Is there a way of keeping this on the desktop without having to do this all the time?  If it helps I have the latest ubuntu version.

---

### Post by viralmeme on 2010-05-08
> **Swiftjay said:**
> So I just got ubuntu installed for the first time, I tried mounting my hard drive to my desktop so i can have easy access to it, but when i restart ubuntu it always dissapears and i have to go to places then click on the hard drive again to mount it to my desktop. 

 Is there a way of keeping this on the desktop without having to do this all the time?  If it helps I have the latest ubuntu version.
You need to add an entry in /etc/fstab

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Morbius1 on 2010-05-08
Need way more information please:

Post the output of the following commands:

> sudo blkid -c /dev/null
cat /etc/fstab
mount

---

### Post by Swiftjay on 2010-05-08
k when i went into the prompt and typed that in, it showed me the hard drive partitions i have.

/dev/sda2: UUID="A2983E3E983E10F1" TYPE="ntfs"

that's the hard drive I want to stay mounted on my hard drive at all times.

when i type in the /etc/fstab command it tells me about typing in blkid -o UUID -s to change to print the UUID name.  When I try to mount /dev/sda2 it say's the directory doesn't exist in /etc/fstab

---

### Post by Morbius1 on 2010-05-08
I only understood one line in your last post so I'm going to give you a general HowTo on automounting an NTFS partition:[I][B]

STEP 1: Find out how the system sees your partitions[/B][/I]

Open **Terminal**
Type **sudo blkid -c /dev/null**

You already did this and the output is:
>  /dev/sda2: UUID="A2983E3E983E10F1" TYPE="ntfs"***STEP 2: Create mount points for your partitions to live in***

Open **Terminal**
Type **sudo mkdir /media/WinDisk**

***STEP 3: Add a line to /etc/fstab/ to have this partition mount at boot:***

```
/dev/sda2 /media/WinDisk ntfs defaults,nls=utf8,umask=007,gid=46 0 0
```This will mount an ntfs partition to /media/WinDisk that will allow all local login users to read and write.

***Step 4: Mount them by executing the new fstab***

Open **Terminal**
Type [B]sudo mount -a

[/B]If the mount -a command gives you any errors then post the output of the following commands as I have already requested:```
cat /etc/fstab
mount                      
```

---

### Post by Swiftjay on 2010-05-08
I tried the /dev/sda2 /media/WinDisk ntfs command but when i tried to enter it said permission denied, considering i'm the root that doesn't make sense to me, lol.

---

### Post by Morbius1 on 2010-05-08
Without the information I requested I can't help you.

---

### Post by Swiftjay on 2010-05-08
k well doing the cat code i got this as my results

/dev/loop0 on / type ext4 (rw,errors=remount -ro)

/dev/sbd1 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0llow - other, blksize=4096)

binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nod)

gvfs-fuse-daemon on /home/jay/ .gvfs type fuse. gvfs-fuse-daemon (rw,nosuid,node user=jay)

/dev/sda2/ on /media/A2983E3E983E10F1 type fuseblk (rw, nosuid, nodev, allow_other blksize=4096,default_permissions)

---

### Post by Morbius1 on 2010-05-09
That is not the output of the "cat code", that is the output of the "mount code".

It appears ( and I may be wrong ) that you installed Ubuntu using Wubi. I know nothing of Wubi.

I would recommend you alter your thread tile to indicate that this is a Wibi install - you're much more likely to attract someone who uses this method to install Ubuntu.:

> mounted hard drive won't show up after reboot - Wubi

---

### Post by viralmeme on 2010-05-10
> **Swiftjay said:**
>  When I try to mount /dev/sda2 it say's the directory doesn't exist in /etc/fstab

Read this thread !!!

**How to fstab** ..

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Swiftjay on 2010-09-20
I solved it by 
mkdir /media/A2983E3E983E10F1

vi /etc/fstab

/dev/sda2       /media/A2983E3E983E10F1 ntfs

Reason why I made that long directory name is cause i'd have to set up my playlist again if I called it another one on rythmbox and that took like an hour to do..lol.  thanks everyone for your help will mark as problem solved.

---

