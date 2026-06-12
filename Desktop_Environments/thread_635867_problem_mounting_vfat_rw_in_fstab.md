---
title: "problem mounting vfat r/w in fstab"
date: 2007-12-09
forum: Desktop Environments
---

### Post by ivago on 2007-12-09
Hi,

I upgraded to Gutsy but now I can't write to my FAT32 partitions, in /etc/fstab I have:```
# /dev/sda8
UUID=4670-56D5  /mnt/downloads  vfat    defaults,utf8,umask=007,gid=1002 0       0
# /dev/sda7
UUID=89D0-E8B2  /mnt/media      vfat    defaults,utf8,umask=007,gid=1002 0       0
```

So now I have a group (1002) where all the users on the system are in who need access to these FAT32 partitions. The only problem is dat I can't write to these partitions. Changing umask to 777 gives no access at all.

All suggestions are appreciated!!

ivago

---

### Post by ivago on 2007-12-09
got it working, apparentely fstab sees ownershiop values different as chmod , so 000 in fstab is like 777 in chmod ...


so fstab now looks like

```
# /dev/sda8
UUID=4670-56D5  /mnt/downloads  vfat    defaults,utf8,umask=000,gid=1002 0       /cdoe0
# /dev/sda7
UUID=89D0-E8B2  /mnt/media      vfat    defaults,utf8,umask=000,gid=1002 0       
```and all users in group 1002 can now read and write on the vfat partitions, 

PS putting 0 0 at the end instead of 0 1 disables the check at boottime.

---

