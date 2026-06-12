---
title: "Problems with Gparted partition sizes"
date: 2009-01-17
forum: General Help
---

### Post by surfgeek on 2009-01-17
So I have resized my XP partition down and then successfully increased the size of my ubuntu partition. Problem is that Gparted says I have resized, but Ubuntu is not reporting the correct free space. Is it possible that Gparted has left temporary files somewhere ?

---

### Post by taurus on 2009-01-17
Post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by surfgeek on 2009-01-17
> **taurus said:**
> Post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

This is the output:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7cda369a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         383     3072000   12  Compaq diagnostics
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         384        5482    40957717+   7  HPFS/NTFS
/dev/sda3            5483       14593    73184107+   5  Extended
/dev/sda5            5483       14504    72469183+  83  Linux
/dev/sda6           14505       14593      714861   82  Linux swap / Solaris

The total disk size is 120gb
XP now has 39gb (sda2)
Ubuntu sda3 is showing 69.79gb of which 54 is used and 15 free. 
Disk Usage Analyser is reporting a system disc size of only 48.7gb with 154gb free . 20gb seems to be missing somewhere.

any help is appreciated.
Thanks

---

### Post by taurus on 2009-01-17
A screenshot of gparted showing the partition table for /dev/sda.

---

### Post by surfgeek on 2009-01-17
I have attached pictures of gparted and disk usage analyzer.

[IMG]http://farm4.static.flickr.com/3384/3203693025_cc6941f4ba_o.jpg[/IMG]

[IMG]http://farm4.static.flickr.com/3340/3203692837_3334127806_o.jpg[/IMG]

---

### Post by taurus on 2009-01-17
```
df -h
```

---

### Post by surfgeek on 2009-01-17
dave@dave-ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              49G   34G   13G  73% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  216K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.8M  498M   1% /dev
tmpfs                 501M  104K  501M   1% /dev/shm
lrm                   501M  2.0M  499M   1% /lib/modules/2.6.27-9-generic/volatile

---

### Post by unutbu on 2009-01-17
It appears the size of the partition /dev/sda5 is 69.11 GiB.
But the size of the filesystem within /dev/sda5 is only 49GB (approx 45.6 GiB).

Sometimes when GParted resizes an ext2/ext3 partition, it for some reason seems to fail to resize the filesystem. If I am understanding your situation correctly, then the problem can be fixed by issuing the command

```

sudo resize2fs /dev/sda5
```

(This command can be safely run even on a mounted filesystem. See "man resize2fs".)

---

### Post by surfgeek on 2009-01-17
Thanks guys, this worked perfectly. I appreciate your help.

Dave

---

