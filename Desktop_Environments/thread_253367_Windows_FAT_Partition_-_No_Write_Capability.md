---
title: "Windows FAT Partition - No Write Capability"
date: 2006-09-08
forum: Desktop Environments
---

### Post by lwsiv on 2006-09-08
So when I set up my installation, I had a vfat partition that I set up for a dual boot (winxp/ubuntu) common data area. I have no issues reading or writing the partition from windows, however, ubuntu allows me to read, but not write the owner is root, group is root, and perms are rwx, rx, rx. I have tried to chown, chgrp, chmod and non of this takes. What do I need to do to set up this partition data area so it can be commonly read, written and executed when I am booted into ubuntu?

---

### Post by Omnios on 2006-09-08
Hi I also have a vfat drive that I use for My DOcuments in XP and a document drive in Linux. I have been using the following fstab entry for over a year now and find it works really well.

```
/dev/hda2       /media/documents     vfat    rw,users,gid=users,umask=000,       0       0
```

 Edit excuse me I just woke up when I posted this and put a gstab typo that should have been fstab.

---

### Post by lwsiv on 2006-09-08
Ok, you are going to have to explain a bit... That was not clear. What is gstab and I have none on my machine. Can you give me a bit more information? I looked in /etc, none exists and I am not sure if I create one will it do anything? What else do I need to set up?

---

### Post by brundles on 2006-09-08
I had a similar problem - really bugged me because it only applied to a certain user. Check the user permissions (Advanced tab I think) under the Users and Groups setting.

If everything looks OK there, make sure the user is part of the plugdev group that Ubuntu seems to use to vfat partitions. (Just type groups from a terminal window).

---

### Post by lwsiv on 2006-09-08
The user and group that Ubuntu assigns ownership to is root. I can't find a way to change that. I have tried (what I think is everything). If I su to root, I can work with the partition, but if I use the pseudo admin account that Ubuntu sets up, I can't (and I would assume any other account).

---

### Post by Omnios on 2006-09-08
> **lwsiv said:**
> Ok, you are going to have to explain a bit... That was not clear. What is gstab and I have none on my machine. Can you give me a bit more information? I looked in /etc, none exists and I am not sure if I create one will it do anything? What else do I need to set up?

 Sorry I corrected that gstab typo it is supposed to be fstab. 
so to acess fstab you type
```

sudo gedit /etc/fstab

``` 
 Also this is a good article explaining how fstab works.
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Also 
```

/dev/hda2       /media/documents     vfat    rw,users,gid=users,umask=000,       0       0

```
/dev/hda2 = is  the partition
/Media/documents is the file the partition mounts to 
vfat is the format type

---

