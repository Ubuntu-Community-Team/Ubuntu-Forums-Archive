---
title: "FSTAB error, makes no sense at all"
date: 2006-07-25
forum: Desktop Environments
---

### Post by dannyboy79 on 2006-07-25
Hello,
I am a newbie so please don't assume anything when trying to help me. Thank you.
I have a 400gb hard drive that is partitioned 3 ways, 1 10gb, 1 swap, and 1 360 gb. It is a SATA drive so they are SDA1, SDA5, and SDA3. I had my fstab calling to mount the 10gb partition to home/daniel/10gb-ext3 using the following line: /dev/sda1	/home/daniel/10gb-ext3	ext3	rw,uid=1000,gid=1000,auto,users,exec,umask=0000	0	0. (i know that there needs to be a tab between each column and that is done correctly despite the fact it may not look like it is) I didn't have the 360 partition mounted yet cause I didn't need it but now I do. I originally formatted it when I did the install. I can even see that it is formated when I go under administration, disks. I actually have even hit format again within that screen cause I couldn't get it to mount but that doesn't help. Anyway, I created a folder /home/daniel/360gb-ext3 and did a chown and chgrp on the folder so that daniel was the owner and group. I added this line to my fstab: /dev/sda3	/home/daniel/10gb-ext3	ext3	rw,uid=1000,gid=1000,auto,users,exec,umask=0000	0	0. When I type sudo mount -a I get an error it states: mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


When I do dmesg | tail as it suggests I get: 
[17294980.144000] EXT3 FS on sda3, internal journal
[17294980.144000] EXT3-fs: mounted filesystem with ordered data mode.
[17294983.524000] kjournald starting.  Commit interval 5 seconds
[17294983.524000] EXT3 FS on sda3, internal journal
[17294983.524000] EXT3-fs: mounted filesystem with ordered data mode.
[17294995.044000] EXT3-fs: Unrecognized mount option "uid=1000" or missing value
[17295039.352000] kjournald starting.  Commit interval 5 seconds
[17295039.352000] EXT3 FS on sda3, internal journal
[17295039.352000] EXT3-fs: mounted filesystem with ordered data mode.
[17295315.312000] EXT3-fs: Unrecognized mount option "uid=1000" or missing value

Which makes no sense because the other sda1 partition mounts fine with those mount options????????? If this helps anyone i did try the following for shits and giggles, if I remove the uid=1000 option and try again, it then complains of the option umask=0000 which again makes no sense as it works for sda1. so I remove that one as well and then it appears to mount. But my question to an expert is, am I going to have the permissions I need? My objective of this folder is basically for storage of my documents, torrents I download, etc etc. I have a seperate hard drive for my movies and music and pics which is formatted FAT32 and ntfs.

](*,) Please help me. Thank you.

---

### Post by philippe_carlo on 2006-07-25
replace
rw,uid=1000,gid=1000,auto,users,exec,umask=0000

by
rw,auto,user

and you should be fine.

---

### Post by sgbeamer on 2006-07-25
I think your problem may be the uid=1000.  This user is the main user (you) but my drives are owned by root and permissions controlled by my directory setting

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext2    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by lamego on 2006-07-25
dannyboy79,
firs let's look on the specific error you are getting.
> [17294995.044000] EXT3-fs: Unrecognized mount option "uid=1000" or missing value
Mount options depend on the file system type, if you read "man mount" you will find that there is no such option as uid or umask for "ext3" file systems, the error message makes all sense.
This options are available for vfat/nfts file systems because they do not support the linux ownership/permissions scheme.

Now talking about what you trying to achieve,if you want a folder available for a particular user inside an ext3 file system just:
```
chmod 755 /home/daniel/10gb-ext3 (write for user, read for everyone)
chown user:group folder
```

---

