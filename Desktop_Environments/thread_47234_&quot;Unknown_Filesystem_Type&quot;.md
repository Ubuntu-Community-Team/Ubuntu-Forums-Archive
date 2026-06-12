---
title: "&quot;Unknown Filesystem Type&quot;"
date: 2005-07-07
forum: Desktop Environments
---

### Post by Trickyphillips on 2005-07-07
Today I backed up a bunch of important files to a second hard drve and re-installed Ubuntu. Once the installation was done, I tried mounting the /dev/sdb1 and got the "must specify filesystem type" message.

I ran gparted to check which filesystem I was using, and it says
> 
[I]Unable to detect filesystem! Possible reasons are:
-The filesystem is damaged
-The filesystem is unknown to libparted
-There is no filesystem available (Unformatted)[/I]


Did the Ubuntu installer format a drive that I didn't tell it to format? I really need this data, as I backed up emails, bookmarks, and many important documents.

Any suggestions?

---

### Post by not_yet on 2005-07-08
run sudo fdisk -l

that should tell you what you have

---

### Post by Trickyphillips on 2005-07-08
[QUOTE=not_yet]run sudo fdisk -l

that should tell you what you have[/QUOTE]
 Thank you.

It says "HPFS/NTFS", but it won't mount when I try "-t ntfs" or "-t hpfs". I believe this may be wrong, as I wrote to it many times (NTFS can't be written in Linux!) before re-installing Ubuntu. I thought it was vfat before I re-installed Ubuntu, but I could be wrong about that.

```

trickyphillips@zion:~$ sudo mount /dev/hdb1 /media/disk -t ntfs
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

trickyphillips@zion:~$ sudo mount /dev/hdb1 /media/disk -t hpfs
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

trickyphillips@zion:~$ dmesg | tail
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hdb1): ntfs_fill_super(): Not an NTFS volume.
HPFS: Bad magic ... probably not HPFS

```

Any solutions? 
Much thanks. :)

---

### Post by Morimando on 2005-07-08
Can you access it in Windows? Did you try - despite the message it was ntfs - to mount using mount -t vfat /dev/X ?

---

### Post by Trickyphillips on 2005-07-08
[QUOTE=Morimando]Can you access it in Windows?[/QUOTE]
I don't want to install Windows if I don't have to, although I will if I must.

[QUOTE=Morimando]
 Did you try - despite the message it was ntfs - to mount using mount -t vfat /dev/X ?[/QUOTE]
I did. :(

---

### Post by Trickyphillips on 2005-07-09
Sorry to bump, but I need these files. :(

---

### Post by hayim on 2006-08-04
Hey, i have similar prob, so maybe my solution will help you..

I have an external haddrive in a case. It was formatted and used in WinXP, and now im trying to access it in Ubuntu. Its loaded as SCSI drive and such, as /dev/sda i think. 

I got same errors as above when i tried to mount. And gparted gave same error of unknown filesystem etc.

Could it be that the partition tables XP wrote on it are not decipherable by Ubuntu? If so, how might I be able to rewrite them nicely?

Perhaps get a live cd of gparted and try to fix the drive in my desktop? Without wiping the many gigabytes of stuff on there? :(

---

