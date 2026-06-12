---
title: "mounting to see partitions"
date: 2009-03-07
forum: General Help
---

### Post by kaykav on 2009-03-07
Good morning,
                       Well here we go again.  I don't know why I have so much trouble with mounting. I want to look at a linux partition (sda7),its just a data storage partition. I give the 'mount ' command,
the output lists sda7  on /boot..Now how do I exactly go about looking at this?...

```
kaykav@vivian:~$ mount -t ext3
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
/dev/sda7 on /boot type ext3 (rw,relatime)
/dev/sda9 on /usr type ext3 (rw,relatime)
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=3e536820-0f38-4e41-9a52-987940f0934e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=bb7fd4a9-534c-4f9e-b940-56bab015cd5d /boot           ext3    relatime        0       2
```


Any other info I'll give ,if needed.   Thank you...Rich

---

### Post by hexanol on 2009-03-07
Well, from what I can see here, sda7 is a partition holding boot-related stuff (since it's mounted on /boot, I would be surprised if it holds *only* "generic" data). You can list the content of the root directory of this partition (well, of the file-system inside your sda7 partition to be precise) with a simple "ls /boot"...

Does this answer your question ? If not, please also post the result of ```
sudo fdisk -l
```

---

