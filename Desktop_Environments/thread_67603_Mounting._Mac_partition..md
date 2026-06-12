---
title: "Mounting. Mac partition."
date: 2005-09-20
forum: Desktop Environments
---

### Post by Conde on 2005-09-20
I know the name of the partition, but how would i mount it? and get it to mount everytime at start up would be helpful?
thanks

---

### Post by oofnik on 2005-09-20
[QUOTE=Conde]I know the name of the partition, but how would i mount it? and get it to mount everytime at start up would be helpful?
thanks[/QUOTE]
 I don't know anything about mac partitions, but if the filesystem is supported it can be mounted. You need to know the dev link (you know, /dev/hda4 or whatever) to the partition to mount it though. I'm half asleep so someone else will be able to help you more :D

---

### Post by cwaldbieser on 2005-09-21
[QUOTE=Conde]I know the name of the partition, but how would i mount it? and get it to mount everytime at start up would be helpful?
thanks[/QUOTE]
The mount command should be able to mount it.  Something like:

```

$ sudo mount -t filesystem-type device mountpoint

```
So, if it were an ext3 filesystem on /dev/hdb1, mounted under /mnt/hdb1:
```
$ sudo mount -t ext3 /dev/hdb1 /mnt/hdb1
``` 
I don't know your filesystem type, but you could just look in "man mount" for the right one (hfs maybe?).
To get it to happen at bootup, you just need to add it to your /etc/fstab.  The starter guide explains what you need to do: [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

