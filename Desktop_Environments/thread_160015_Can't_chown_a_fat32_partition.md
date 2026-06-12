---
title: "Can't chown a fat32 partition"
date: 2006-04-14
forum: Desktop Environments
---

### Post by Bubba Ho-Tep on 2006-04-14
I can't change the permissions on a Fat32 partition I have mounted for sharing files between Windows and Ubuntu.

This is the output from "ls -l"
drwxr-xr-x  7 root root 8192 1970-01-01 08:00 FAT32

when i try to chown the files in the partition I get "operation not permitted"

the exact command I'm using is 

"sudo chown -R doug: FAT32"

where doug is the username and FAT32 is the foldername

Just in case I was missing something I tried doing it thru the GUI - I opened Nautilus as root and tried to change the owner  of FAT32 - same deal.

The partition isn't mounted read only (root can write to files ok - I checked) my fstab entry is:

/dev/hdb1   /home/doug/FAT32   vfat   defaults   0       0


so errrr what am I missing?

BHT

---

### Post by dermotti on 2006-04-14
I didn't know you could even set permissions on fat32......

---

### Post by aysiu on 2006-04-14
You can't *chown* Windows partitions.

[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by vayu on 2006-04-14
[QUOTE=Bubba Ho-Tep]
The partition isn't mounted read only (root can write to files ok - I checked) my fstab entry is:

/dev/hdb1   /home/doug/FAT32   vfat   defaults   0       0
BHT[/QUOTE]

I tried a bunch of things till I finally got it working in Samba the way I needed so, some of the following things might be unneccessary.  At any rate I have the following for fstab:

instead of "defaults" I have "user,rw,umask=000,uid=username,gid=username"

In your case that would give you:
```
/dev/hdb1   /home/doug/FAT32   vfat   user,rw,umask=000,uid=doug,gid=doug   0       0
```

I also had to go into Windows command window and do an: 

```
attrib -r fat32directoryname

```

to get rid of a read only attribute that the fat32 directory had in windows (don't ask me why).

---

### Post by Bubba Ho-Tep on 2006-04-14
Cheers vayu, that did the trick. The partition is now mounted with doug as owner and I've full read/write permissions which is what I wanted. I can't chown it so I guess aysiu is right - you learn something new every day!

---

