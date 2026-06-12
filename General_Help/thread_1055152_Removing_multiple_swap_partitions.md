---
title: "Removing multiple swap partitions"
date: 2009-01-30
forum: General Help
---

### Post by Sherina on 2009-01-30
Hello everyone I am currently running ubuntu 7.10. I had upgraded to 8.04 but I didn't like it so I switched back to 7.10. I did a clean install, removing the partition, repartitioning the drive and reinstalling 7.10 and ended up with 2 swap partitions. How do I remove one of them and which one do I remove?

---

### Post by taurus on 2009-01-30
You probably have two entries for swap partitions in /etc/fstab so if you want to remove one, do it from there.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```

---

### Post by Sherina on 2009-01-30
I don't know what to remove. this is what it looks like:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=bddcd730-830a-42a9-8ebf-1da51e644db9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=d874acaa-84e3-466e-8806-d915c828c92c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

in g-parted I have a linux swap 5 and a linux swap 6

---

### Post by taurus on 2009-01-30
> **Sherina said:**
> I don't know what to remove. this is what it looks like:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=bddcd730-830a-42a9-8ebf-1da51e644db9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
**[COLOR="Blue"]UUID=d874acaa-84e3-466e-8806-d915c828c92c none            swap    sw              0       0[/COLOR]**
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

You only have one swap partition.  What makes you think you have two?  Post the outputs of these commands from a terminal.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
free -m
```

---

### Post by drs305 on 2009-01-30
It looks like you only have one swap listed in fstab. You can check to see if you have two separate swap partitions.

Run the following commands:
```

sudo blkid -c /dev/null # see what partitions you have and if you have more than one 'swap' partition
*If you do:*
gksudo gparted   # start gparted

```

Find the swap partition you want to delete.
It should  *not* be UUID=d874aca...  (maybe /dev/sda2). You will have two partitions designated "swap" in the blkid command above. You want to delete the one with a different UUID.
Click on it to select it, then "Partitions", "Swapoff". 
Highlight and select it again, the "Partition", "Delete".

---

### Post by dabl on 2009-01-30
There are multiples answers:

a. Two swap partitions are harmless,

b. taurus has showed you how to stop mounting one of them, but it will be sitting there as a partition on your hard drive, and 

c. You could do (b.) above, and then you can use GParted or Qparted and delete one of the swap partitions from the hard drive, HOWEVER be very careful if you take this approach.  You need to be certain that the one you delete from /etc/fstab is the SAME one you delete with Gparted. If you're not comfortable or experienced doing disk partitioning, then the best advice would be to refer to (a.).

:)

---

### Post by Sherina on 2009-01-30
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3f1c4404

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13063   104928516    7  HPFS/NTFS
/dev/sda2           13064       14454    11173207+  83  Linux
/dev/sda3           14455       14593     1116517+   5  Extended
/dev/sda5           14523       14593      570276   82  Linux swap / Solaris
/dev/sda6           14455       14522      546147   82  Linux swap / Solaris

Partition table entries are not in disk order
sherina@sherina-laptop:~$ sudo blkid
/dev/sda1: UUID="78508E56508E1B50" LABEL="Windows XP" TYPE="ntfs" 
/dev/sda2: UUID="bddcd730-830a-42a9-8ebf-1da51e644db9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="76a422e5-d647-4f72-8163-4bacbb98782f" 
/dev/sda6: TYPE="swap" UUID="d874acaa-84e3-466e-8806-d915c828c92c" 

```

```

/dev/sda1: UUID="78508E56508E1B50" LABEL="Windows XP" TYPE="ntfs" 
/dev/sda2: UUID="bddcd730-830a-42a9-8ebf-1da51e644db9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="76a422e5-d647-4f72-8163-4bacbb98782f" 
/dev/sda6: TYPE="swap" UUID="d874acaa-84e3-466e-8806-d915c828c92c" 

```

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=bddcd730-830a-42a9-8ebf-1da51e644db9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=d874acaa-84e3-466e-8806-d915c828c92c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
sherina@sherina-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           438        422         16          0          7        103
-/+ buffers/cache:        311        127
Swap:          533         32        500

```

---

### Post by drs305 on 2009-01-30
*/dev/sda5* is the one you would delete if you decide to do so.

---

### Post by taurus on 2009-01-30
If you decide to delete that extra swap partition, what are you going to do with the space?  Bet it's not a whole lot of space since it's a logical partition.  If you want to use that space for /, then you have to resize your extended partition, meaning you must unmount the other swap partition first from the LiveCD, then shrink your extended partition and expend your root partition, /dev/sda2, to take up that unallocated space.

Do you want to do all that or can you live with two swap partitions?

---

### Post by drs305 on 2009-01-30
I won't go into the details here but one use of a small partition is to make a SystemRescueCD or gpartedCD partition which allows you to boot to those 'rescue' apps directly from the grub menu, without having to insert a rescue CD or the ubuntu LiveCD to use gparted on system partitions. These partitions take less than 300MB of space.

---

