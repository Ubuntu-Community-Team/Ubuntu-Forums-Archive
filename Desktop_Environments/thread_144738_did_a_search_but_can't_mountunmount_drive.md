---
title: "did a search but can't mount/unmount drive"
date: 2006-03-14
forum: Desktop Environments
---

### Post by McOwnage on 2006-03-14
I want to mount a drive i have that is NTFS it has my un2k4 on it and want to copy the maps i got to the linux version but every time i try to mount it i get /dev/hdc already mounted or /media/hdd2 busy

can some one please help me 

I have seen it asked so i will post

fdisk -l
```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/hdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       11784    94654948+  83  Linux
/dev/hdb2           11785       12161     3028252+   5  Extended
/dev/hdb5           11785       12161     3028221   82  Linux swap / Solaris

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       14593   117218241    7  HPFS/NTFS

```

fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```
Trying to follow the help to mount it and read/copy but not to have it mounted all the time

---

### Post by Sutekh on 2006-03-15
Okay if you don't want this mounted all the time then forget the /etc/fstab

Use this command to mount the drive as you need it
```
sudo mount [COLOR="Navy"]/dev/hdc1[/COLOR] /media/hdc1 -t ntfs -o nls=ut8,umask=0222
```
This will mount /dev/hdc1 (this is the one you want?) to the [COLOR="Navy"]/media/hdc1[/COLOR] folder, which you will need to create prior to this with ```
sudo mkdir [COLOR="Navy"]/media/hdc1[/COLOR]
```(You can use another place if you like, [COLOR="Navy"]/media/hdc1[/COLOR] was just a suggestion)

You won't be able to write to it (being NTFS) but will be able to read and copy the files across.

To unmount the drive when you're done with it, use
```
sudo umount /dev/hdc1
```

---

### Post by McOwnage on 2006-03-15
first TY for reply and it did not work :cry: 
I want to read the 120gig drive
did what you suggested and got 
```
mcownage@ubuntu:~$ sudo mkdir /media/hdc1
Password:
mcownage@ubuntu:~$ sudo mount /dev/hdc1 /media/hdc1 -t ntfs -o nls=ut8,umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```
did what it suggested Dmesg | tail and here is what i got
```
mcownage@ubuntu:~$ dmesg | tail
[4311626.667000] NVRM: Xid: 27,  L2 -> L2 temp 110C
[4313074.162000] NVRM: Xid: 27,  L2 -> L2 temp 109C
[4313227.054000] NVRM: Xid: 27,  L2 -> L2 temp 109C
[4327160.309000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4327160.309000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4327160.384000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4327160.384000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4327187.054000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4327187.087000] Unable to load NLS charset ut8
[4327187.087000] NTFS-fs error (device hdc1): parse_options(): NLS character set ut8 not found.
mcownage@ubuntu:~$

```

---

### Post by mozetti on 2006-03-15
it's supposed to be
```
utf8
```

typo :)

---

### Post by McOwnage on 2006-03-15
Thank you very much

---

### Post by Sutekh on 2006-03-15
Ah thanks for finding that mozetti!  

Typing at work is sketchy at best, I have a KVM switch that makes my keyboard work have sticky keys.  (I actualy 'lost' 6 characters in this post alone!)

---

