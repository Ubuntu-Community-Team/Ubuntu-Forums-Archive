---
title: "Lost swap after dual boot"
date: 2008-12-07
forum: General Help
---

### Post by kelean on 2008-12-07
I had Ibex installed and running happily.  I then wanted to play around with Kubuntu.  So I installed it on my computer now I am dual booting Ubuntu and Kubuntu.  Everything is running great except that now when I boot unbuntu my swap is not enabled.  I have to enable it with the swopon command with every boot.

How do I make it enabled at boot time again.

Thanks Kelean.

---

### Post by taurus on 2008-12-07
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
free
```

---

### Post by kelean on 2008-12-07
Okay here they are.

```
kevin@ububox12:~$ sudo fdisk -l
[sudo] password for kevin: 

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00021ab7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1228     9863878+  83  Linux
/dev/sda2            1229        2434     9687195    5  Extended
/dev/sda5            2343        2434      738958+  82  Linux swap / Solaris
/dev/sda6            1229        2288     8514387   83  Linux
/dev/sda7            2289        2342      433723+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

```
kevin@ububox12:~$ sudo blkid
/dev/sda1: UUID="62e2ca1d-c89e-4ccf-a08f-0ac50ebec813" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="be7b6e53-e1b9-438e-b6e4-58032841a531" 
/dev/sda6: UUID="975d91e7-ab4c-42aa-9da7-1a663240c4e0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="f37eae4d-d930-4929-af0e-47b4b69d7ca6" 

```

```
kevin@ububox12:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=62e2ca1d-c89e-4ccf-a08f-0ac50ebec813 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4452a508-1f22-43c5-b4e2-79ab551dcccc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

```
kevin@ububox12:~$ free
             total       used       free     shared    buffers     cached
Mem:        253360     247648       5712          0       2276      66580
-/+ buffers/cache:     178792      74568
Swap:       738948      28300     710648

```

---

### Post by taurus on 2008-12-07
I think when you installed Kubuntu, you probably have the installer reformatted the original swap partition, /dev/sda5.  As a result, the UUID changed.  So, you need to edit /etc/fstab and replace the old UUID for /dev/sda5 with the new one.

```

UUID=be7b6e53-e1b9-438e-b6e4-58032841a531  none   swap   sw   0   0

```
And since you also have a second swap partition, might as well use it.  Add this line to the end of your /etc/fstab.

```

UUID=f37eae4d-d930-4929-af0e-47b4b69d7ca6  none  swap  sw  0  0

```
Save it and reboot. Then, look at your swap space.

```
free
```

---

### Post by kelean on 2008-12-07
taurus, thanks so much.  That worked great and I also added the second swap just for fun. 

```
kevin@ububox12:~$ free
             total       used       free     shared    buffers     cached
Mem:        253360     250188       3172          0       1880      55092
-/+ buffers/cache:     193216      60144
Swap:      1172660       7224    1165436

```

It gives me some extra swap.  Thanks for the quick answer I appreciate it.

Kelean.

---

### Post by frejock on 2008-12-07
<moved post to new thread..sorry>

---

