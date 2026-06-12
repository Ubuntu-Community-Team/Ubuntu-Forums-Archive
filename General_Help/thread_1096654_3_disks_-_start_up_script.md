---
title: "3 disks - start up script?"
date: 2009-03-15
forum: General Help
---

### Post by lazylew on 2009-03-15
Using Hardy Heron 8.04

I have 3 hard disks. After login the 2 extra ones always appear in the "Places" menu, but apparently aren't mounted properly.
When I refer to a location (file or folder) on one of them, the computer doesn't find it till I click that disk in the Places menu (then it remains active throughout the session).

Is there a script I could use that automatically starts up these disks?
It's annoying the way it is now, because I put my separate Home folder on one of those disks too (and possibly did it wrong?)

---

### Post by hyper_ch on 2009-03-15
paste the output of:

```

sudo fdisk -l

```

```

df -h

```

```

cat /etc/fstab

```

---

### Post by lazylew on 2009-03-15
> **hyper_ch said:**
> paste the output of:

```

sudo fdisk -l

```
```

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f8000b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9835    78999606   83  Linux
/dev/sda2            9836       10011     1413720    5  Extended
/dev/sda5            9836       10011     1413688+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x963e963e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1282    10297633+  83  Linux
/dev/sdb2            4679        4865     1502077+   5  Extended
/dev/sdb3            1283        4678    27278370   83  Linux
/dev/sdb5            4679        4865     1502046   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          13      104391   83  Linux
/dev/sdc2              14          78      522112+  82  Linux swap / Solaris
/dev/sdc3              79       14593   116591737+  83  Linux
```
> **hyper_ch said:**
> paste the output of:

```

df -h

```
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             9.8G  3.3G  6.1G  36% /
varrun                629M  224K  629M   1% /var/run
varlock               629M     0  629M   0% /var/lock
udev                  629M   88K  629M   1% /dev
devshm                629M  264K  629M   1% /dev/shm
lrm                   629M   40M  590M   7% /lib/modules/2.6.24-23-rt/volatile
/dev/sdb3              26G  407M   25G   2% /home
gvfs-fuse-daemon      9.8G  3.3G  6.1G  36% /home/ludo/.gvfs
/dev/sdc3             112G   69G   44G  62% /media/disk
```

and cat /etc/fstab:
 ```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=18686b15-ac28-4b5c-b294-7a499d50d5af /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d387594d-f3e8-4a41-8fd9-821e4a23867d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/sda3 /home ext3 nodev,nosuid 0 2 dit was de oude setting ivm bootprobleem nieuwe lijn is hieronder
UUID=01e842a7-4b26-42bb-926c-5617a63b19eb /home ext3 nodev,nosuid 0 2
```

---

### Post by hyper_ch on 2009-03-15
when posting the output of a command or some text file enclose it each in [noparse]```

```[/noparse] brackets. that makes it simpler to read.

---

### Post by lazylew on 2009-03-15
> **hyper_ch said:**
> when posting the output of a command or some text file enclose it each in [noparse]```

```[/noparse] brackets. that makes it simpler to read.
okido, sorry; I'll try and remember next time

---

### Post by hyper_ch on 2009-03-15
do you have multiple distros installed?

Best is to add the other partitions to your fstab and then have them mounted at places where you want them to be

e.g. /dev/sdb3 as /media/sdb3

```

sudo mkdir /media/sdb3

```

then edit the /etc/fstab and add an entry like
```

/dev/sdb3 /media/sdb3 ext3 nodev,nosuid 0 2

```

---

### Post by lazylew on 2009-03-15
> **hyper_ch said:**
> do you have multiple distros installed?
I noticed in the output I sent that there's mention of Solaris, but I haven't installed that (??).
Apart from Ubuntu Hardy Heron I also downloaded Xubuntu to try out Xfce, so Ubuntu should be the only distro working.

> Best is to add the other partitions to your fstab and then have them mounted at places where you want them to be

e.g. /dev/sdb3 as /media/sdb3

```

sudo mkdir /media/sdb3

```then edit the /etc/fstab and add an entry like
```

/dev/sdb3 /media/sdb3 ext3 nodev,nosuid 0 2

```That's going to take me some research, because I haven't got too many clues about partitioning and how I want them.
I'll be gone shortly and will have to find time to take a closer look at this sometime during the week.

Thanks for the help so far :)

---

### Post by hyper_ch on 2009-03-15
well, sdb and sdc have both SWAP partitions (that has nothing to do with solaris) so you might want to reorganize them also can create one huge primary partition on there..

---

### Post by lazylew on 2009-03-15
> **hyper_ch said:**
> well, sdb and sdc have both SWAP partitions (that has nothing to do with solaris) so you might want to reorganize them also can create one huge primary partition on there..
If I understand correctly I need only one SWAP-partition in total; ok.
I'll have to do some more reading on partitioning though, before I do something stupid  ;)

---

### Post by hyper_ch on 2009-03-15
you can have as many as you want... but if you have space enough to have one swap partition on one disk I don't see much reason to add more on others also..

---

