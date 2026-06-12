---
title: "New External Drive, No Permissions."
date: 2006-07-29
forum: Desktop Environments
---

### Post by bradshaw on 2006-07-29
I'm trying to reformat this drive (/dev/sdc1) in EXT3 with access path home/user/external using Disk Manager.

"are you sure you want to format Partition 1 (/dev/sdc1)?"

I click yes

Then it says the drive is formatting, when it's done I recieve this error
Couldn't find "/tmp/disks-conf-sdc1"
Please Check the spelling and try Again. 

I try to access /home/user/external and I have no permissions

What am I doing wrong and how do I get permission?

---

### Post by bradshaw on 2006-07-29
I've tried looking at the other topics regarding this but I can't make sense out of them.

I type these commands in the Terminal 

sudo -s
man chown
man chgrp

but I can't make any sense out of man chown or man chgrp

---

### Post by cptnapalm on 2006-07-29
The best bet is probably to apt-get install gparted.  Then use that to delete the partition, create a new one and format it.

As I am assuming that it is a USB external drive, I think it will automatically mount it in /media.  That's what mine does, anyhow.

---

### Post by zudduz on 2006-07-29
Is any other accounts logged on when you try to work with the drive?  if so log them off first I have been having similar problems with my USB Card reader

---

### Post by bradshaw on 2006-07-29
Yes, an external drive, and no there are no users other than me.

in gparted I select /dev/sdc (194474 MB)
I select the partition, I unmount it, then I delete it,
Then I make a new partition, 
Create as: Primary Partition
Filesystem: ext3
Free Space PReceding (MB): 0
New Size (MB): 194474
Free Space Fallowing (MB): 0
then I click add.
then I click apply.

Then it applys pending operations, 

Create Primary Partition #1 (ext2, 194474) on /dev/sdc

mkfs.ext2 /dev/sdc1

then I leave the computer for awhile and now that window is gone and now I seem to have a newly formated partition for this external hard drive.

Now what do I do? It still seems as if I have no permission

---

### Post by bradshaw on 2006-07-30
I still have no permissions on this hard drive and I don't know what to do from here.

---

### Post by bradshaw on 2006-07-30
[http://www.linuxhelp.net/newbies/newbies-print.php#perms](http://www.linuxhelp.net/newbies/newbies-print.php#perms)

this worked.

---

