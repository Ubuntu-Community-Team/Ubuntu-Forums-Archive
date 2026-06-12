---
title: "unwanted partition visible in nautilus but not mounted"
date: 2006-08-03
forum: Desktop Environments
---

### Post by m.musashi on 2006-08-03
I have posted a similar issue [here](http://ubuntuforums.org/showthread.php?t=224457) but as there seem to be two separate issues I was advised to start a new thread.

In short, the root partition for my suse install shows up in the nautilus browser (places -> computer (see screenshot)) but is not accessible. If I try to access it I get the message "unable to mount the selected volume." It also says,
```
error: device /dev/hdc6 is not removable
error: could not execute pmount
```
It is not a removable drive so I'm not even sure why it is showing up at all. I had the same problem with the /home partition of my suse install but once I added that partition to /etc/fstab the problem was solved. In this case, I don't want that partition to mount or show up at all. It is there even though there is no entry for it in /etc/fstab or anywhere else that I can see, but if I do add it to /etc/fstab it will mount properly.

The other problem is that my shared partition mounts as DSK2_VOL1. All the other partitions seems to use a name scheme that includes the name of the /media folder where they around mounted. This is the only one that does not follow that scheme. It's not a huge issue but it's frustrating to not understand why or make it do what I want.

The current state of my /etc/fstab looks like this:
```
jim@number6:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
#Added by diskmounter utility
/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0
#Added by diskmounter utility
/dev/hdc1 /media/files vfat iocharset=utf8,umask=000 0 0

/dev/hdc7 /media/suse_home reiserfs defaults 0 0
```

Any help would be appreciated.
Thanks.

EDIT: By the way, the drive labeled "14.2 GB Volume" is the suse root partition I am referring to.

---

### Post by DrMilo on 2006-09-03
I'm looking for the same answer.

---

