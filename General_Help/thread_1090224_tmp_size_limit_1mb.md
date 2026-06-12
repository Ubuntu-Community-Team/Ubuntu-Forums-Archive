---
title: "/tmp size limit 1mb"
date: 2009-03-08
forum: General Help
---

### Post by HeretikSaint on 2009-03-08
My file system is no where near out of memory yet when I try to download something from Firefox, Firefox will display a dialog box that says "There is no enough room on the disk for /tmp/filename.part.deb".  I checked /tmp and there is a 1mb size limit.  Is there any reason why?  How do I fix this problem.  I know it's not the entire file system because I can copy stuff from my external hard drive to my file system.  Any ideas?  Thanks for the help.

---

### Post by sdennie on 2009-03-08
What is the output of:

```

df
cat /etc/fstab

```

It's possible you are mounting parts of the filesystem in strange ways.

---

### Post by HeretikSaint on 2009-03-08
> **sdennie said:**
> What is the output of:

```

df
cat /etc/fstab

```

It's possible you are mounting parts of the filesystem in strange ways.
Here is the output of both:
```
user@user-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                      28097104  26327956    353136  99% /
varrun                 1030700       112   1030588   1% /var/run
varlock                1030700         0   1030700   0% /var/lock
udev                   1030700        84   1030616   1% /dev
devshm                 1030700        12   1030688   1% /dev/shm
lrm                    1030700     44984    985716   5% /lib/modules/2.6.24-23-generic/volatile
overflow                  1024      1024         0 100% /tmp
gvfs-fuse-daemon      28097104  26327956    353136  99% /home/user/.gvfs
/dev/sdg1            117211808  80694336  36517472  69% /media/USERS BACKUP
/dev/scd1               307936    307936         0 100% /media/cdrom1
user@user-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by sdennie on 2009-03-08
This post should fix your problem: [http://ubuntuforums.org/showpost.php?p=5546144&postcount=4](http://ubuntuforums.org/showpost.php?p=5546144&postcount=4)

---

### Post by HeretikSaint on 2009-03-08
> **sdennie said:**
> This post should fix your problem: [http://ubuntuforums.org/showpost.php?p=5546144&postcount=4](http://ubuntuforums.org/showpost.php?p=5546144&postcount=4)

Thank you I'll check it out now.  I will post back here my results.

---

### Post by HeretikSaint on 2009-03-08
edit:  It worked thank you very much.

---

