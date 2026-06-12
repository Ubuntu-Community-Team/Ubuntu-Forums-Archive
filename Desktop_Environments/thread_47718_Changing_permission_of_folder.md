---
title: "Changing permission of folder"
date: 2005-07-09
forum: Desktop Environments
---

### Post by Prudentissimus on 2005-07-09
Hello,

How do I change permission on a Folder which is on a FAT32 partition I have mounted to /mnt/windows2?

I want to be able to write/read/delete 

-Thanks.

---

### Post by rider343 on 2005-07-09
[http://pt-br.ubuntuguide.org/#mountunmountfat](http://pt-br.ubuntuguide.org/#mountunmountfat)

---

### Post by swamp on 2005-07-10
[QUOTE=Prudentissimus]Hello,

How do I change permission on a Folder which is on a FAT32 partition I have mounted to /mnt/windows2?

I want to be able to write/read/delete 

-Thanks.[/QUOTE]
 Have you read the man page for chmod? If I recall correctly, directories must be executable.

Try:

chmod 777 [directory filepath]

---

### Post by adwait on 2005-07-10
MAybe u should edit ur fstab and change the uid to 1000 and gid to 1000....

---

### Post by SS2 on 2005-07-10
Or you can change the permitions of the /mnt/windows2 folder to 777?

---

### Post by rider343 on 2005-07-10
sudo gedit /etc/fstab
change

default:

umask=000     


restart your machine

---

### Post by Morimando on 2005-07-10
[QUOTE=rider343]sudo gedit /etc/fstab
change

default:

umask=000     


restart your machine[/QUOTE]
right. I mount FAT32 like this
```
/dev/sda5       /media          vfat            user,auto,noatime,rw,umask=000  0       2
```
maybe some option(s) in there is/are unnecessary, but it works.

And: You can skip trying the "wohooo why don't you just chmod 777, N00b" - posts above, because on a FAT32 there's no such thing as per-user-permissions, so no use for chmod  \\:D/

---

### Post by Prudentissimus on 2005-07-10
[QUOTE=Morimando]right. I mount FAT32 like this
```
/dev/sda5       /media          vfat            user,auto,noatime,rw,umask=000  0       2
```
maybe some option(s) in there is/are unnecessary, but it works.

And: You can skip trying the "wohooo why don't you just chmod 777, N00b" - posts above, because on a FAT32 there's no such thing as per-user-permissions, so no use for chmod  \\:D/[/QUOTE]
 what does "user", "noatime", "rw", mean?



EDIT:  By the way, there are only 2 folders on the /mnt/windows2 which I cannot edit. I think those 2 are locked because I copied them from a CD...

---

### Post by Morimando on 2005-07-11
[QUOTE=Prudentissimus]what does "user", "noatime", "rw", mean?



EDIT:  By the way, there are only 2 folders on the /mnt/windows2 which I cannot edit. I think those 2 are locked because I copied them from a CD...[/QUOTE]
fascinating.. maybe chmod a+rw works on the two folders? Else set writing permissions in Windows for the folders.
user means that a normal user can mount and unmount the drive, rw means it gets mountes read/write and noatime means "Do  not  update  inode  access  times on this file system (e.g, for faster access on the news  spool  to  speed  up                news servers)."

---

