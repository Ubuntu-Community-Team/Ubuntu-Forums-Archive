---
title: "mounting windows partition on boot"
date: 2006-08-22
forum: Desktop Environments
---

### Post by davidshere on 2006-08-22
I have a Dell Dimension 3000, which came with Windows XP pre-installed.  Installing Ubuntu on a second hard drive, I've found that Ubuntu mounts the two XP recovery partitions quite effectively, but the main XP partition is mounted with no permissions except for the root user.

Searching these forums, I've found the fix:

sudo umount /dev/hdb2
sudo mount /dev/hdb2 /media/dell/ -t ntfs -o umask=0222

which works great!  How do I get this to load this way automagically on boot, so I don't have to run these commands myself?

---

### Post by waldschm on 2006-08-22
to add these changes to boot, you need to edit your fstab file which controls much of the mount process during boot:

```
sudo gedit /etc/fstab
```

now search in this file for your ntfs drive, /dev/hdb2. Now search in that row for where it says umask=007 or whatever it may say and change it to 0222.

---

### Post by aysiu on 2006-08-22
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) has full instructions.

---

### Post by davidshere on 2006-08-22
Working!  Thanks... =D>

---

