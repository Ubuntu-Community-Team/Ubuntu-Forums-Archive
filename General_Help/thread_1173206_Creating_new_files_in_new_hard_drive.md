---
title: "Creating new files in new hard drive"
date: 2009-05-29
forum: General Help
---

### Post by Mattyk on 2009-05-29
Hi, I'm a complete noob to the Ubuntu world and as such I have a noobish question:

Hi recently added a second hard drive to my 9.04 version and I figured out how to change the permissions so that I can read and write to the drive (I think). However, I am unable to create new folders within the drive to keep it organized! What do I need to do to be able to accomplish this? 


just for reference the string I used to change permissions was this one:

```
sudo chown -R username:username /media/Docs
```with username being whatever my username is and /media/Docs being the mount point...


EDIT: Also how do I keep the drive mounted when I reboot or shutdown?

---

### Post by Chronon on 2009-05-29
chown is a program to change ownership of a folder, not permissions.  Investigate chmod instead, as that allows you to set read/write/execute permissions for owner, group, user or all.

Edit: You can't keep it mounted per se.  You can automount it each time you boot, however.  I did this not too long ago by adding an entry to the fstab.

---

### Post by Mattyk on 2009-05-29
..so what would the string look like if I was to do it the way you are directing?

---

### Post by Ansraliant on 2009-05-29
As Chronon said you need to use chmod, here's a link that explains how to use it:

```

http://www.ss64.com/bash/chmod.html

```

Good Luck!

---

### Post by Mattyk on 2009-05-29
OK I'll go ahead and read up on that website and ask any question after in this thread! 

As far as the mounting goes, how would I go about adding an entry to the fstab? Or should I just manually mount it each time?

---

### Post by fuzzyworbles on 2009-05-29
just edit /etc/fstab and copy the entry for, say, your /home partition, but just change the device and mount locations accordingly.

---

### Post by Mattyk on 2009-05-29
Ok so I figured out how to make it so I can create new files and folders as well as write to and read from the drive:

```
sudo chown $user:$user /media/Docs
```This seems to be working great. Now how do I go about making the drive auto mount?

---

### Post by John.Michael.Kane on 2009-05-29
> **Mattyk said:**
> Ok so I figured out how to make it so I can create new files and folders as well as write to and read from the drive:

```
sudo chown $user:$user /media/Docs
```This seems to be working great. Now how do I go about making the drive auto mount?

```
sudo fdisk -l
```
look for (/dev/hda hdb sda sdb 1 or 2 or number shown for the Linux partition you want to use.

You can use gparted to find out if the partition on the new drive is ext3 or ext2, if you do not know.

Backup your fstab
```
sudo cp /etc/fstab /etc/fstab_backup
```
Then run
```
sudo nano /etc/fstab
```

Add the below line edited to match your partition setup.
```
/dev/ using one of the following hda hdb sda sdb /media/Docs ext3 defaults 0 0
```

---

### Post by Mattyk on 2009-05-29
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0d48db91-a1e2-411a-a099-c6305b4f723b /               ext3    relatime,erro$
# swap was on /dev/sda5 during installation
UUID=7537e9c3-46a6-46d3-9abf-723c477d8d45 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0





                               [ Read 14 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

```

This is what comes up after I do the second to last step.

Where do I add:

/dev/sdb/media/Docs ext3 defaults 0 0

---

### Post by John.Michael.Kane on 2009-05-29
> **Mattyk said:**
> ```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0d48db91-a1e2-411a-a099-c6305b4f723b /               ext3    relatime,erro$
# swap was on /dev/sda5 during installation
UUID=7537e9c3-46a6-46d3-9abf-723c477d8d45 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
**/dev/sdb    /media/Docs ext3 defaults 0 0**




                               [ Read 14 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

```

This is what comes up after I do the second to last step.

Where do I add:

/dev/sdb/media/Docs ext3 defaults 0 0

Make sure that sdb is the proper partition, usually when a drive is partitioned whole you end-up sdb1.

Anyway the line in bold is where you would place your /dev line.

---

### Post by Mattyk on 2009-05-29
Ok I did that and sorry for the ultra stupid question...how do I enter and exit it into the terminal? when I hit enter it just does a hard return...

I feel really dumb...

---

### Post by Mattyk on 2009-05-29
bump...

I've tried just exiting out but it doesn't keep the setting..

---

### Post by Mattyk on 2009-05-29
got it!! ctrl +x, now I just gotta restart and see if that worked!

---

### Post by Mattyk on 2009-05-29
it worked!!! now I just gotta figure out how to do all this stuff on my own!

---

### Post by John.Michael.Kane on 2009-05-29
> **Mattyk said:**
> it worked!!! now I just gotta figure out how to do all this stuff on my own!

Glad it worked, as for learning it will come to you take your time, if you are stumped, and a forum search does not reveal answers then post a thread.

---

### Post by Slim Odds on 2009-05-29
> **Ansraliant said:**
> As Chronon said you need to use chmod, here's a link that explains how to use it:

```

http://www.ss64.com/bash/chmod.html

```Good Luck!

Why not make that link a link?

[http://www.ss64.com/bash/chmod.html](http://www.ss64.com/bash/chmod.html)

---

