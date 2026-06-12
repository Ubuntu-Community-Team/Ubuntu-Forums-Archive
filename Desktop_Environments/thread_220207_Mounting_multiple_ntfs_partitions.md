---
title: "Mounting multiple ntfs partitions"
date: 2006-07-21
forum: Desktop Environments
---

### Post by Lard on 2006-07-21
On my windows machine i partitioned the hard drive into 3 (Op Sys, My Docs, Music).

I have followed instructions and can mount MyDocs sucessfully.  

However I can't mount the other two partitions.

Could someone expalin simply :)  ho to do this

thanks a lot

andrew

---

### Post by mogelhead on 2006-07-21
First, can you please post the output of the following command:
```
sudo fdisk -l
```

---

### Post by Kelnoky on 2006-07-21
Well. First you have to make a directory for every partition you want to mount. Best with "sudo mkdir /home/yourname/whatever/". 
Then you look up what your device names are with "sudo fdisk -l". 
Since you already mounted one partitions you should know the names of the other partitions, or at least how to figure them out.
Assuming you want to auto-mount those partitions every time you boot into ubuntu you have to open the fstab with "sudo gedit /etc/fstab".
There you need to add a path like:
```
/dev/hdx1       /whatever_path_you_like     ntfs    ro,user,auto,nls=utf8,uid=1000,gid=1000  0  0
```

The x in "hdx" standing for the proper letter you got out of the fdisk list. After adding the line for every partition you can try it out with entering "sudo mount -a" into a terminal. If any error pops up, check the spelling of your lines in fstab, then it should work. ;)
Now you can reboot and the partitions should be mounted every time. :)

---

### Post by Lard on 2006-07-21
here's the results from sudo fdisk:

Disk /dev/hda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1208     9703228+   7  HPFS/NTFS
/dev/hda2            1787        4982    25671870    f  W95 Ext'd (LBA)
/dev/hda3            1209        1786     4642785   83  Linux
/dev/hda5            1817        3364    12434278+   7  HPFS/NTFS
/dev/hda6            3365        4982    12996553+   7  HPFS/NTFS
/dev/hda7            1787        1816      240912   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Kelnoky on 2006-07-21
Well then, you can just copy my line in the fstab as I posted with "hda5" and "hda6" instead of "hdx". ;) And of course you need to make a directory for every partition before that.

---

### Post by Lard on 2006-07-21
nice, thanks very much

---

### Post by Lard on 2006-07-21
hmmm, some problems:  Have copied/pased and altered appropriately what you said but get the bash 'Permission denied'

I'm logged on with full privelages and have entered password etc.

---

### Post by Dimitar on 2006-10-17
hey lard, 
are you using the command sudo infront of your arguments?

---

