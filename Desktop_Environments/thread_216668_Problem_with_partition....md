---
title: "Problem with partition..."
date: 2006-07-15
forum: Desktop Environments
---

### Post by Varox on 2006-07-15
Hi everyone, i started using linux like a year ago, i finally decided that i wanted to get rid of Win... 

I have my HD splited in half, in one of the partitions i had win, i formated that partition to ext3, no problem there.... the problem is i can mount the partition but i can't write on it...

the partition is /dev/hda1 and is mounted in /media/disk2

a cannot even create a dir as sudoer, i get this: mkdir: cannot create directory `/media/disk2/bosta': Read-only file system

how can i fix this?

Thankx a lot!

---

### Post by DavidFL on 2006-07-15
Hello.  Can you post the result of

```

cat /etc/fstab

```

and
```

ls -la /media

```

from the terminal shell ?

---

### Post by Varox on 2006-07-15
cat /etc/fstab
 
<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/disk2    ext3    ro,user        0       0
/dev/hda1       /media/windows  vfat  iocharset=utf8,umask=000  0    0

ls -la /media

drwxr-xr-x  7 root root 4096 2006-07-13 02:33 .
drwxr-xr-x 21 root root 4096 2006-07-05 03:59 ..
lrwxrwxrwx  1 root root    6 2005-09-19 19:03 cdrom -> cdrom0
dr-xr-xr-x  1 root root 2048 2005-09-01 16:56 cdrom0
drwxr-xr-x  2 root root 4096 2005-09-19 19:03 cdrom1
drwxr-xr-x  3 root root 4096 2006-07-13 03:00 disk2
lrwxrwxrwx  1 root root    7 2005-09-19 19:03 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2005-09-19 19:03 floppy0
drwxr-xr-x  2 root root 4096 2005-09-20 15:28 windows

---

### Post by DavidFL on 2006-07-15
> **Varox said:**
> cat /etc/fstab
 
<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/disk2    ext3    ro,user        0       0
/dev/hda1       /media/windows  vfat  iocharset=utf8,umask=000  0    0

ls -la /media

drwxr-xr-x  7 root root 4096 2006-07-13 02:33 .
drwxr-xr-x 21 root root 4096 2006-07-05 03:59 ..
lrwxrwxrwx  1 root root    6 2005-09-19 19:03 cdrom -> cdrom0
dr-xr-xr-x  1 root root 2048 2005-09-01 16:56 cdrom0
drwxr-xr-x  2 root root 4096 2005-09-19 19:03 cdrom1
drwxr-xr-x  3 root root 4096 2006-07-13 03:00 disk2
lrwxrwxrwx  1 root root    7 2005-09-19 19:03 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2005-09-19 19:03 floppy0
drwxr-xr-x  2 root root 4096 2005-09-20 15:28 windows

In your /etc/fstab file you have:

> 
/dev/hda1 /media/disk2 ext3 ro,user 0 0


The "ro" portion means "read only".  remove the ro and give it a go. unmounting and then remounting.

Make sure to backup your old /etc/fstab first:

```

sudo cp /etc/fstab /etc/fstab.july152006.bak

```

then edit /etc/fstab to remove the ro and save it:

```

sudo gedit /etc/fstab

```

or (good to know a non-X editor)

```

sudo pico /etc/fstab

```

Then unmount the device.

```

sudo umount /dev/hda1

```

Finally remount it and give it a try:

```

sudo mount /dev/hda1

```

Also check your permissions on the mount point.

---

