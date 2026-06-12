---
title: "Formatting and mounting new harddrive"
date: 2005-10-26
forum: Desktop Environments
---

### Post by Moonbuzz on 2005-10-26
Hello, I've decided to take one of the 2 non-Linux HD and format it to use with Ubuntu (The experience I had since Breezy was released made me want to migrate). 
The question is a: how do I format the harddrive (Currently NTFS) to ext3 (maybe will be easier to format it to FAT32?) 
and b: how do I mount it without it being referred as an external HD? I would like it to be an integral part, and not /media/hdb1 or something, for convenience reasons.

Any input will be welcomed.

---

### Post by mlomker on 2005-10-26
If you do **sudo fdisk -l** in a terminal then you can see what the device is.  After that it's just **sudo mkfs.ext3 /dev/hdX**.

If you want to mount it to a directory then make a directory and then edit your /etc/fstab to specify what directory to mount it to.

---

### Post by Moonbuzz on 2005-10-26
[QUOTE=mlomker]If you do **sudo fdisk -l** in a terminal then you can see what the device is.  After that it's just **sudo mkfs.ext3 /dev/hdX**.[/QUOTE]Thanks, I'll try that.

> If you want to mount it to a directory then make a directory and then edit your /etc/fstab to specify what directory to mount it to.
That's no problem, I'm familiar with fstab. What I wanted was a more integral mount. If possible, that if I have 2 HD of 20 GB, the system will act like it has one 40GB HD when it installs stuff etc.

---

### Post by mlomker on 2005-10-26
> If possible, that if I have 2 HD of 20 GB, the system will act like it has one 40GB HD when it installs stuff etc.

It doesn't work that way in linux.  You mount partitions to directories.  

You could mount it to /home or some other large directory if you wish.  What you'd do is rename /home after booting up into 'rescue' mode and then creating a blank /home...then update your fstab to mount the new drive there...then after mounting the new drive to /home you copy your data from the renamed /home to the new one...then delete the old directory.

---

### Post by Moonbuzz on 2005-10-27
> **mlomker]It doesn't work that way in linux.  You mount partitions to directories.  [/quote]
Yea, I sort of figured that one out. But never hurts to try  said:**
> You could mount it to /home or some other large directory if you wish.  What you'd do is rename /home after booting up into 'rescue' mode and then creating a blank /home...then update your fstab to mount the new drive there.

Thanks, 
Just to see if I got it, I need to reboot to 'rescue', then mv /home to /homebackup, mkdir /home, edit fstab to mount the new harddrive as /home?

---

### Post by RAOF on 2005-10-27
[QUOTE=Moonbuzz]...If possible, that if I have 2 HD of 20 GB, the system will act like it has one 40GB HD when it installs stuff etc.[/QUOTE]
That actually is possible, but not unless you've set it up beforehand.  IIRC, LVM (logical volume manager) does precisely what you're after - you add discs to a logical disc, and it just looks like the disc grew bigger.

However, in order to set that up, I believe you'd need to format your existing drives.  And I've never set it up before, so you'd better look into it yourself.

---

### Post by Moonbuzz on 2005-10-27
[QUOTE=RAOF]That actually is possible, but not unless you've set it up beforehand.  IIRC, LVM (logical volume manager) does precisely what you're after - you add discs to a logical disc, and it just looks like the disc grew bigger.

However, in order to set that up, I believe you'd need to format your existing drives.  And I've never set it up before, so you'd better look into it yourself.[/QUOTE]

I'll leave that to the next installation,  then, and do what mlomker suggested.

---

### Post by Moonbuzz on 2005-10-27
The formatting was extremely painless, however, I want to merge the two partitions into one, currently I have hdb5 and hdb6, I wonder if I can format both of them into one partition.

---

### Post by mlomker on 2005-10-27
> hdb5 and hdb6, I wonder if I can format both of them into one partition.

Sure, if they are on the same physical drive.  You can run **cfdisk** and delete both partitions and create one larger one...and then format it.

---

### Post by az on 2005-10-27
You will have to use parted to delete the last partition and then make the other one that much bigger.  After that, just put a filesystem on your new fat partition.

You cannot use parted if the disk is mounted.  If one of the two partitions is your linux partition, fire up the installer cd.  Let it get to the point where it asks you about partitioning and then do CTRL-ALT-F2 and run
parted /dev/hda

the do 
print
and it wil list your partitions
rm 
will remove a partitions
resize 
will... guess what?
mkpartfs will make a filesystem on a partition.

reboot and you are good to go.

---

### Post by az on 2005-10-27
[QUOTE=mlomker]Sure, if they are on the same physical drive.  You can run **cfdisk** and delete both partitions and create one larger one...and then format it.[/QUOTE]
...Beat me to it.  You can do that too....

---

### Post by Moonbuzz on 2005-10-28
I've tried cfdisk and got a bit confused as to what it exactly did. Finally I downloaded GParted and that fixed all the problems.

---

