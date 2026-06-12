---
title: "Problems in mounting a new ext3 partition."
date: 2005-08-17
forum: Desktop Environments
---

### Post by GoA on 2005-08-17
I deleted my big ntfs partition with windows to get more space to ubuntu. Then i created one ext3 partition and one fat partition. I easily managed to get the fat partition to work but ext3 gives me the trouble. I just can't get write permissions for me, only to root. I tried many different configurations wich I found with the search but they didnät help me. Here is a copy of my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/hda4       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hda1 /media/varasto ext3 defaults 0 0

The last one is the one with problems. The disknumber is right. Theres only one 60 g partition and that it is. Also the path /media/varasto does exists. I created it with command sudo mkdir bla blaa. Could somebody help me please. :) 

BTW, bye bye windows.

---

### Post by fig_jam_uk on 2005-08-17
Hi you could always try on that last line

/dev/hda1 /media/varasto ext3 rw,user 0 0

i had the same problem so i formatted as ext2 and all is good  \\:D/ 

let me know if this works

---

### Post by GoA on 2005-08-18
[QUOTE=fig_jam_uk]Hi you could always try on that last line

/dev/hda1 /media/varasto ext3 rw,user 0 0

i had the same problem so i formatted as ext2 and all is good  \\:D/ 

let me know if this works[/QUOTE]
 Didn't work. Next I try to use Gparted to change it into ext2.

Ok, I changed it into ext2 with Gparted now so how can i edit fstab to mount ext2 partition?

Thanks for the help.

EDIT: Won't work. Here's fstab 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/hda4       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hda1       /media/varasto  ext2    defaults 0 1

And sudo fdisk -l

harri@hki2-8-4-41:~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1            2551       10199    61440592+  83  Linux
/dev/hda2   *           1        2442    19615333+  83  Linux
/dev/hda3            2443        2550      867510    5  Extended
/dev/hda4           10200       14593    35294805   83  Linux
/dev/hda5            2443        2550      867478+  82  Linux swap / Solaris

Partition table entries are not in disk order

I try to use the hda1 60 gigs partition. I have created the varasto folder. Do I have to format new partitions after using gparted or will it do it automatically? Because I haven't formated anhything. :D

---

### Post by zAo on 2005-08-18
Change the permissions of the directory you mount your partition on!

---

### Post by GoA on 2005-08-18
[QUOTE=zAo]Change the permissions of the directory you mount your partition on![/QUOTE]
 I tried, I just didn't managed to get the right code to it.

---

### Post by kostkon on 2005-08-18
If you want to be ext3, then format it again as ext3, put again */dev/hda1 /media/varasto ext3 defaults 0 0* in fstab and then change the group of the folder /media/varasto (where you mount your partition) from **root** to **users**  group. Then give read-write permissions to the group.

Then I think you'll be OK.

If your are not confident with changing groups etc., someone, of course,can help you with the commands.

---

### Post by GoA on 2005-08-18
I put sudo chmod 777 /media/varasto and it works now. Thanks for all the help guys. :)

---

