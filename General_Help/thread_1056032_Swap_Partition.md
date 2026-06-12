---
title: "Swap Partition"
date: 2009-01-31
forum: General Help
---

### Post by hyperdude111 on 2009-01-31
When i first set up my install I decided not to have swap space becaue i had used all the primary partitions in gparted. Anyway i decided yesterday to delete on of these and create 2 extended partitions, one of these is swap. However ubuntu does not recognise this new partition and so it is still not used as swap space. What i want to know is how can i tell ubuntu to use this partition. 

Thanks.

---

### Post by taurus on 2009-01-31
You have to edit /etc/fstab and add entry for your new swap partition.  Open a terminal and post the outputs of these commands.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
free -m
```

---

### Post by RoyalPro on 2009-01-31
You need to have something in your /etc/fstab that looks like this:
```
# /dev/sdc3
UUID=b44fb480-c770-45e5-b17e-a0fa9c3ef87 none            swap    sw,pri=1        0       0
```
Where the UUID is the one for the partition of the swap or you can use the /dev/....

---

### Post by hyperdude111 on 2009-01-31
sudo fdisk -l
Disk /dev/sda: 360.0 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9670    77674243+   7  HPFS/NTFS
/dev/sda2            9671       18147    68091502+   5  Extended
/dev/sda3           18148       42421   194980905   83  Linux
/dev/sda4           42422       43777    10892070    7  HPFS/NTFS
/dev/sda5            9671       10052     3068383+  82  Linux swap / Solaris
___________
sudo blkid
Disk /dev/sda: 360.0 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9670    77674243+   7  HPFS/NTFS
/dev/sda2            9671       18147    68091502+   5  Extended
/dev/sda3           18148       42421   194980905   83  Linux
/dev/sda4           42422       43777    10892070    7  HPFS/NTFS
/dev/sda5            9671       10052     3068383+  82  Linux swap / Solaris
hugo@hugo-desktop:~$ sudo blkid
/dev/sda1: UUID="A0C0F33BC0F315EE" LABEL="HP" TYPE="ntfs" 
/dev/sda3: LABEL="Ubuntu" UUID="5c305e12-68dc-43a2-91fa-75593d12d4f2" TYPE="ext3" 
/dev/sda4: UUID="949CA48C9CA46A86" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/sdf1: UUID="48BD-9D5E" TYPE="vfat" 
/dev/sda5: UUID="9ab6d26f-595a-492d-91c1-a6a6d94e3c85" TYPE="swap"
_____________
cat /etc/fstab
/dev/sda1: UUID="A0C0F33BC0F315EE" LABEL="HP" TYPE="ntfs" 
/dev/sda3: LABEL="Ubuntu" UUID="5c305e12-68dc-43a2-91fa-75593d12d4f2" TYPE="ext3" 
/dev/sda4: UUID="949CA48C9CA46A86" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/sdf1: UUID="48BD-9D5E" TYPE="vfat" 
/dev/sda5: UUID="9ab6d26f-595a-492d-91c1-a6a6d94e3c85" TYPE="swap" 
hugo@hugo-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=5c305e12-68dc-43a2-91fa-75593d12d4f2 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
_________

free -m
             total       used       free     shared    buffers     cached
Mem:          1881       1842         39          0         44        890
-/+ buffers/cache:        906        975
Swap:            0          0          0

---

### Post by taurus on 2009-01-31
Edit /etc/fstab (I am assuming you are running Gnome)

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
UUID=9ab6d26f-595a-492d-91c1-a6a6d94e3c85   none   swap   sw   0   0
```
Save it and close down gedit.  Then activate your new swap partition.

```
sudo mount -a
free -m
```

---

### Post by hyperdude111 on 2009-01-31
Thank you for this after re-boot it all worked perfectly. You saved me a long time googling. I can now run multiple virtual machines and desktop managers without the fear of a system lockup. Thanks.

---

