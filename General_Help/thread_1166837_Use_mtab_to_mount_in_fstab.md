---
title: "Use mtab to mount in fstab?"
date: 2009-05-22
forum: General Help
---

### Post by BLTicklemonster on 2009-05-22
Can I take the information in mtab (after I've mounted all my drives) and just drop it in fstab and save it and have my drives mounted on boot?

Example:

my fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=28dd1ff9-9709-4c9f-8724-ee4a409b18f4 /               reiserfs notail,relatime 0       1
# /dev/sdb2
UUID=a205df67-db8e-43a4-b17d-d5124b4340d0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

my mtab
```

/dev/sdb1 / reiserfs rw,relatime,notail 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/bill/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=bill 0 0
/dev/sda8 /media/disk fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda5 /media/disk-1 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda6 /media/disk-2 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda2 /media/disk-3 reiserfs rw,nosuid,nodev,uhelper=hal 0 0
/dev/sda7 /media/disk-4 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda1 /media/disk-5 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdc1 /media/disk-6 reiserfs rw,nosuid,nodev,uhelper=hal 0 0

```

new fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=28dd1ff9-9709-4c9f-8724-ee4a409b18f4 /               reiserfs notail,relatime 0       1
# /dev/sdb2
UUID=a205df67-db8e-43a4-b17d-d5124b4340d0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda8 /media/disk fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda5 /media/disk-1 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda6 /media/disk-2 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda2 /media/disk-3 reiserfs rw,nosuid,nodev,uhelper=hal 0 0
/dev/sda7 /media/disk-4 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdc1 /media/disk-6 reiserfs rw,nosuid,nodev,uhelper=hal 0 0

```

Would that work okay? And if so, how hard would it be for ubuntu to offer this as an option in system>administration...

---

### Post by BLTicklemonster on 2009-06-14
Huh. I was really expecting an answer. I'd rather get a straightforward answer than try and do this all over again and have to do a bunch of needless editing.

---

### Post by loomsen on 2009-06-14
Why shouldn't it work? Try it, monitor your systemlog for possible errors.

You'll probably have to create a initrd capable of fuseblk for example (don't know, don't use it)

mkinitrd initrd-custom-`uname -r`.img `uname -r`

Follows:
mkinitrd <outputfilename> <kernel to build against>

```
man mkinitrd
```

I used it to include btrfs in my initrd for example.

lsinitrd </path/to/initrd-to-view> 

will output the content of your initrd (ls -l of the included files and the nash script running during boot)

You'd probably want to redirect the output to a file for better handling

lsinitrd </path/to/initrd-to-view>  > some-fancy-filename-log

---

### Post by unutbu on 2009-06-15
BLTicklemonster, whenever you have an NTFS partition, /etc/mtab will use the word "fuseblk" where you'd normally expect the filesystem type. If you transfer the mtab line 
```

/dev/sdc1 /mnt fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
```

directly into your /etc/fstab and then try to mount it with
```

sudo mount -a
```
, you will get this error:
```

mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

However, if you change the word "fuseblk" to "ntfs", then when you run
```

sudo mount -a
```

to mount all partitions listed in /etc/fstab, you will get this warning:

```
WARNING: blksize option is ignored because ntfs-3g must calculate it.
```

but the partition will be mounted successfully despite the warning.

---

### Post by BLTicklemonster on 2009-06-15
Thank you unubtu, that was what I was looking for. I knew there was a catch, and I was hoping someone would enlighten me. I've done it before but getting ntfs instead of fuseblk was a tedious thing to have to figure out on my own.

---

