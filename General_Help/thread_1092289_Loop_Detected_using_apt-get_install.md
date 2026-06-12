---
title: "Loop Detected using apt-get install"
date: 2009-03-10
forum: General Help
---

### Post by ZeddZull on 2009-03-10
I have installed a pristine version of 8.10 onto a server with the following configuration:

X86 processor
2 500GB harddrives - partitioned as:
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             48062440    938044  44682920   3% /
tmpfs                   257028         0    257028   0% /lib/init/rw
varrun                  257028       308    256720   1% /var/run
varlock                 257028         0    257028   0% /var/lock
udev                    257028      2752    254276   2% /dev
tmpfs                   257028         0    257028   0% /dev/shm
/dev/sdb1             48062440    236700  45384264   1% /boot
/dev/md0             384586164  26482556 338567768   8% /home
/dev/md1              46141312    666044  43131392   2% /var
/dev/sdc3            114406124 113630172    775952 100% /mnt/disk1

```

md0 and md1 are RAID1 partitions that I am using for my /home and /var directories.  /boot is on its own partition as is /  These are not part of the RAID1 arrays.

When I try to do ```
sudo apt-get install base-files
``` (or any other apt-get install), I get a seemingly infinite list of ```
find: File system loop detected
``` as shown below:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
base-files is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 84 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up base-files (4.0.4ubuntu2.2) ...
find: File system loop detected; `/boot/dev/fd/3/lib/udev/devices/fd' is part of the same file system loop as `/boot/dev/fd'.
find: File system loop detected; `/boot/dev/fd/3/usr/X11R6/bin/X11' is part of the same file system loop as `/boot/dev/fd/3/usr/X11R6/bin'.
find: File system loop detected; `/boot/dev/fd/3/usr/bin/X11' is part of the same file system loop as `/boot/dev/fd/3/usr/bin'.
.
.
.

```

Looking at ```
ls -l /boot/dev/fd
``` shows

```

lrwxrwxrwx 1 root root 13 2009-03-09 12:51 /boot/dev/fd -> /proc/self/fd

```

following the link, I see

```

lrwx------ 1 derek derek 64 2009-03-10 08:50 0 -> /dev/pts/0
lrwx------ 1 derek derek 64 2009-03-10 08:50 1 -> /dev/pts/0
lrwx------ 1 derek derek 64 2009-03-10 08:50 2 -> /dev/pts/0
lrwx------ 1 derek derek 64 2009-03-10 08:50 255 -> /dev/pts/0

```

As you can see, there is no "3" directory, so this must get created on the fly, but it seems to then link back to /boot/dev/fd, which creates an infinite loop.

Any ideas on how to solve this problem so that I can actually install software?

Thanks.

---

### Post by k7k0 on 2010-05-28
Been late, but I've this problem in a box. I finally managed to upgrade killing the find process

---

