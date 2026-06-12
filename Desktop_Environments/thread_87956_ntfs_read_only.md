---
title: "ntfs read only"
date: 2005-11-09
forum: Desktop Environments
---

### Post by n_hendrick on 2005-11-09
Heres the situation, I have a read only filesystem mounted as /mnt/xp. I want to give read access to my home account,but I can't change the ownership or the properties of the mount. I've tried to alter my fstab file to mount the drive as rw, but to no avail. 
Anybody have any experience with ntfs? I thought I could just change the properties of the mount, but the chmod command isn't altering the drive at all. Is there something I'm missing?

---

### Post by Pablo_Escobar on 2005-11-09
NTFS filesystem is available in read-only at that point in Linux.
You may look at captive ntfs, but from what I've heared it's unstable and can mess up Your data.

---

### Post by n_hendrick on 2005-11-09
is there a way to give read permission to a user account aside from the root account?

---

### Post by psusi on 2005-11-09
man mount.  You will want to add either umask=, gid=, or uid= options to the mount options in your fstab to instruct the filesystem what uid and gid should own all the files ( instead of root ) or what the pemissions on the files should be ( instead of owner only access ).

---

### Post by DrBair on 2005-11-09
Model your fstab line after this:

/dev/hda1       /mnt/windows    ntfs    user,auto,umask=0000    0       0

Most important part in there is 'umask=0000' which gives permissions to everyone.  'user' gives users the right to mount/umount the partition and 'auto' will make it mount at boot. If you'd like you can also make that 'noauto' and you will then have to mount explicitly. 


About captive...
I never had any data loss with it, but it is SLOW! Like 50KB/s slow. NTFS is a bit complex and written in circles so writting the driver is no small task.  We have fast read and write support to it, but the writing is still too flakey for regular use.  Hopefully we'll get working driver sooner than later.

---

### Post by frodon on 2005-11-09
Add a line like that in your /etc/fstab file, /dev/hda1 is the name of your partition and /mnt/ntfs the repertory where the partition will be mounted :```
/dev/hda1 /mnt/ntfs_disk ntfs nls=utf8,user,auto,umask=0222 0 0
```Then do a "sudo mount -a" to remount all the partition declared in the fstab file.

EDIT : there's some guy's here who are really quick  to answer ;)

---

### Post by n_hendrick on 2005-11-09
thanks guys....I now have read permission...thanks again for all your help.

---

### Post by michaelharg on 2005-11-09
Hey, im really struggling with this, it seems like it should be so easy but never works for me!

I just want read only access to my windows drive... Here's my etc /etc/fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/hda5     ntfs    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
```

How should i edit it to allow the access i want?

Thanks

---

### Post by Irony on 2005-11-09
Here's my file, it works fine, ntfs is read only:

[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0
/dev/hda1       /mnt/XPa  ntfs    nls=utf8,umask=0222 0       0
/dev/hda3       /mnt/XPb  ntfs    nls=utf8,umask=0222 0       0
/dev/hdb1       /mnt/2nd  vfat    defaults,umask=000  0       0
/dev/hda4       /mnt/Ubb      ext3    defaults        0       0[/PHP]

I assume you have created your folders, e.g. I first made a folder called XPa;

*sudo mkdir /mnt/XPa*

If the folders don't exist the partitions can't mount.

---

### Post by ilja on 2005-11-12
I'm having the same problem. But...
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    nls=utf8,umask=0222        0       0
/dev/hda2       /media/hda2     ntfs    nls=utf8,umask=0222        0       0
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

```

ilja@uvatha:~$ sudo mount -a
ilja@uvatha:~$

```

```

ilja@uvatha:~$ ls /media/hda1/
ls: /media/hda1/: Permission denied
ilja@uvatha:~$ ls /media/ -l
total 68
lrwxrwxrwx  1 root root     6 2005-11-12 10:28 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2005-11-12 10:28 cdrom0
dr-x------  1 root root 20480 2005-11-12 07:55 hda1
dr-x------  1 root root 45056 2005-11-10 08:11 hda2
ilja@uvatha:~$

```

So, what next?

---

### Post by ilja on 2005-11-12
Well, apparently a reboot fixed it, mount -a wasn't enough.

---

### Post by slux on 2005-11-12
I'm pretty sure mount is happy if a given filesystem is mounted in the first place, changing the mount options in fstab won't cause a remount and that's why "mount -a" won't do the trick.

---

