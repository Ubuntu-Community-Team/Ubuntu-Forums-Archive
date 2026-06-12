---
title: "Win Mount problems"
date: 2007-11-22
forum: Desktop Environments
---

### Post by NJC on 2007-11-22
Trying to mount my Win drive in Gutsy 7.10 using the following in fstab:

```
#/dev/sdb1       
UUID=1610-375D  /media/windows  vfat    iocharset=utf8,umask=000   0       0

```It seemed to work once and today it bombed out again. Error saying I don't have permission to mount this drive .](*,)

Here's fdisk - l:


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         605     4859631   83  Linux
/dev/sda2             606         681      610470   83  Linux
/dev/sda3             682         784      827347+  82  Linux swap / Solaris

[delthehell]

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5170    39085168+   c  W95 FAT32 (LBA)

---

### Post by bingoUV on 2007-11-22
What did you do to get that error? Was it something like this ?
```

sudo mount /media/windows

```


Add sudo if you missed it earlier.

---

### Post by NJC on 2007-11-22
When I try to use sudo mount the error is "/media/windows/ doesn't exist." The permissions error is from Nautilus - right click, Mount and "you do not have permission to mount this drive." Not sure if that's the exact error, but close.

---

### Post by bingoUV on 2007-11-22
Nautilus never gave me any option to mount, but maybe it is a misconfiguration on my part. To make the partition mountable by any user, change the fstab entry to 
```

#/dev/sdb1       
UUID=1610-375D  /media/windows  vfat    user,iocharset=utf8,umask=000   0       0

```Now, nautilus might be able to mount the partition. Now you can also mount the filesystem using the command
```

mount /media/windows 

```
Or, if you do not want to edit fstab, you could try mounting from terminal using sudo like I suggested in my earlier post.

---

