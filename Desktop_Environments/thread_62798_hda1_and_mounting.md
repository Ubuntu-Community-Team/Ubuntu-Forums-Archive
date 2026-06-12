---
title: "hda1 and mounting"
date: 2005-09-05
forum: Desktop Environments
---

### Post by kb7ypf on 2005-09-05
Hello all-

Just a quick question and I hope there is a great answer.

When I boot up Ubuntu, it loads (almost) perfect and everything works fine
                                         except
my "C" vfat drive is not mounted and does not show up on the Desktop as the other media drives do.

I have edited a program called Maxtor and made an executable out of it.
I entered the following line: ** /dev/hda1  /mnt/C-Drive**
This mounts the "C" drive, because it is not mounted at Ubuntu startup.

So my question is:  
1.  How do I get Ubuntu to mount "C" drive at start up?
2.  How do I get the "C" drive to show up on the Desktop?

Thanks again for your help.  From my very limited knowledge and experience Ubuntu Distro is really Super.  Also, now 100% away from Bill Gates  \\:D/ 



Dick

---

### Post by arnieboy on 2005-09-05
[QUOTE=kb7ypf]Hello all-

Just a quick question and I hope there is a great answer.

When I boot up Ubuntu, it loads (almost) perfect and everything works fine
                                         except
my "C" vfat drive is not mounted and does not show up on the Desktop as the other media drives do.

I have edited a program called Maxtor and made an executable out of it.
I entered the following line: ** /dev/hda1  /mnt/C-Drive**
This mounts the "C" drive, because it is not mounted at Ubuntu startup.

So my question is:  
1.  How do I get Ubuntu to mount "C" drive at start up?
2.  How do I get the "C" drive to show up on the Desktop?

Thanks again for your help.  From my very limited knowledge and experience Ubuntu Distro is really Super.  Also, now 100% away from Bill Gates  \\:D/ 



Dick[/QUOTE]

paste the contents of the following:
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by kb7ypf on 2005-09-05
Thanks for your response.  
Here is the sudo fdisk -l:

Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         959        3649    21615457+   c  W95 FAT32 (LBA)
/dev/hda2               2         958     7687102+   5  Extended
/dev/hda5   *           2         958     7687071   83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 81.9 GB, 81963515904 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2492    20016958+   c  W95 FAT32 (LBA)
/dev/sda2            2493        9963    60010807+   f  W95 Ext'd (LBA)
/dev/sda5            2493        2550      465853+  83  Linux
/dev/sda6            2551        5042    20016958+   b  W95 FAT32
/dev/sda7            5043        5053       88326   82  Linux swap / Solaris
/dev/sda8            5054        5100      377496   83  Linux
/dev/sda9            5101        7650    20482843+   b  W95 FAT32
/dev/sda10           7651        9963    18579141    b  W95 FAT32

Here is cat /etc/fstat:

kb7ypf@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               reiserfs notail          0       1
/dev/sdb7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0


Hope this helps you out.

Thanks again,
Dick

---

### Post by arnieboy on 2005-09-05
[QUOTE=kb7ypf]Thanks for your response.  
Here is the sudo fdisk -l:

Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         959        3649    21615457+   c  W95 FAT32 (LBA)
/dev/hda2               2         958     7687102+   5  Extended
/dev/hda5   *           2         958     7687071   83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 81.9 GB, 81963515904 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2492    20016958+   c  W95 FAT32 (LBA)
/dev/sda2            2493        9963    60010807+   f  W95 Ext'd (LBA)
/dev/sda5            2493        2550      465853+  83  Linux
/dev/sda6            2551        5042    20016958+   b  W95 FAT32
/dev/sda7            5043        5053       88326   82  Linux swap / Solaris
/dev/sda8            5054        5100      377496   83  Linux
/dev/sda9            5101        7650    20482843+   b  W95 FAT32
/dev/sda10           7651        9963    18579141    b  W95 FAT32

Here is cat /etc/fstat:

kb7ypf@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               reiserfs notail          0       1
/dev/sdb7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0


Hope this helps you out.

Thanks again,
Dick[/QUOTE]
just one more question: look at the output of sudo fdisk -l and let me know which drive/drives u want mounted automatically. u have two hard disks. which of the window partitions do u to refer to as ur C: drive?

---

### Post by kb7ypf on 2005-09-05
Here is what I have:

A hard disk drive with WIN98SE on one partition and Linux on approximately 7.3 GB of the same hard drive (hda).  This is denoted as drive "C".  What I want is to load linux and then have the FAT32 portion of "C" drive to be loaded by linix.  I am not sure about hda2 or hda5.  They look to be the same to me.  I'm not sure why two are showing up.  Maybe something wrong with the partition table on this drive.

I have a USB Moxtor 80GB hard drive that I partitioned into four each 20GB drives.  It appears that they are found and loaded by linux at start up time, and show up on my Desktop.  I don't have any problem with the Maxtor 4 drives loading or showing up.

Hope this helps out.
Thanks once again,
Dick

---

### Post by arnieboy on 2005-09-05
[QUOTE=kb7ypf]Here is what I have:

A hard disk drive with WIN98SE on one partition and Linux on approximately 7.3 GB of the same hard drive (hda).  This is denoted as drive "C".  What I want is to load linux and then have the FAT32 portion of "C" drive to be loaded by linix.  I am not sure about hda2 or hda5.  They look to be the same to me.  I'm not sure why two are showing up.  Maybe something wrong with the partition table on this drive.

I have a USB Moxtor 80GB hard drive that I partitioned into four each 20GB drives.  It appears that they are found and loaded by linux at start up time, and show up on my Desktop.  I don't have any problem with the Maxtor 4 drives loading or showing up.

Hope this helps out.
Thanks once again,
Dick[/QUOTE]
gotcha. do the followin:
```
sudo mkdir /media/C:
sudo gedit /etc/fstab
```
add the following line after the last line:
> /dev/hda1       /media/C:  vfat    umask=000      0       0
save and exit. reboot.
I dont think u care too much abt seeing the C: drive icon on ur desktop. but anytime u wanna access it, just go to /media/C: from nautilus or terminal and u will have read/write access to your C: drive.
EDIT: if u get a kick out of seeing the mounted drives on your desktop do the following:
go to System Tools--> Configurations Editor
and go to apps-->nautilus-->desktop and **check** volumes visible.

---

### Post by WebbyBabe on 2005-09-06
I tried doing the following by following the directions, but I don't get any type of hard drives listed on my desktop. There's no sda1 or sda2 on my desktop. I went to app -> nautilius and clicked to make the volumes visible with no luck. 

Here is my result of fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7755    62292006    7  HPFS/NTFS
/dev/sda2           13160       19262    49022347+  83  Linux
/dev/sda3            7756       13159    43407630   83  Linux

Partition table entries are not in disk order


And the result of cat /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdb        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
 /dev/sda1 /media/C: vfat umask=000 0 0


*EDIT* - I forgot to add that when I go to ~/media/c: there's no files listed.

---

### Post by arnieboy on 2005-09-06
[QUOTE=WebbyBabe]I tried doing the following by following the directions, but I don't get any type of hard drives listed on my desktop. There's no sda1 or sda2 on my desktop. I went to app -> nautilius and clicked to make the volumes visible with no luck. 

Here is my result of fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7755    62292006    7  HPFS/NTFS
/dev/sda2           13160       19262    49022347+  83  Linux
/dev/sda3            7756       13159    43407630   83  Linux

Partition table entries are not in disk order


And the result of cat /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdb        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
 /dev/sda1 /media/C: vfat umask=000 0 0[/QUOTE]
those directions were not for u. which drive do u want to mount?

---

### Post by WebbyBabe on 2005-09-06
I want to mount my windows drive. sda1

---

### Post by bored2k on 2005-09-06
[QUOTE=WebbyBabe]I want to mount my windows drive. sda1[/QUOTE]
 Execute the commands in Terminal mode (Applications -> System Tools -> Terminal)
1. ```
sudo mkdir /media/NTFS
```
2. ```
sudo gedit /etc/fstab
```
** Append the following lines:
3. ```
/dev/sda1       /media/NTFS  ntfs    nls=utf8,umask=0222 0       0
```
4. ```
sudo mount -a
```

---

### Post by WebbyBabe on 2005-09-06
Thank you! It worked, but I don't get a hard drive icon on my desktop.

---

### Post by bored2k on 2005-09-06
[QUOTE=WebbyBabe]Thank you! It worked, but I don't get a hard drive icon on my desktop.[/QUOTE]
 In Hoary sometimes you get, sometimes you don't. In Breezy wich will be the next Ubuntu (in a month) you will get it for sure though.

Nice substitutes:
A.
1. Open firefox
2. Click on Open
3. Look for your Drive then click ADD.
This will make it load in your Places menu on your upper panel

B.
1. ```
sudo /etc/init.d/dbus-1 restart
```Will do the same as above.

And by the way, that drive is NTFS formatted, wich means you only get read only support. If you ever change it to FAT filesystem, that fstab line needs to change.

---

### Post by WebbyBabe on 2005-09-06
Ah. Thank you. I now have an icon to my HD on my desktop.

---

### Post by kb7ypf on 2005-09-06
Hello arnieboy-

Back at again.  Your last e-mail in part said:
[B]gotcha. do the followin:
Code:

sudo mkdir /media/C: sudo gedit /etc/fstab


add the following line after the last line:
Quote:
/dev/hda1 /media/C: vfat umask=000 0 0

save and exit. reboot.
I dont think u care too much abt seeing the C: drive icon on ur desktop. but anytime u wanna access it, just go to /media/C: from nautilus or terminal and u will have read/write access to your C: drive.
EDIT: if u get a kick out of seeing the mounted drives on your desktop do the following:
go to System Tools--> Configurations Editor
and go to apps-->nautilus-->desktop and check volumes visible.[/B]

I followed your instructions and it worked.....Mucho Thanks

However my flavor of Ubuntu down not display "nautilus" under Apps.  I must be missing it.  I looked very hard for it, but it is not listed under any folder displayed under Applications. 

So the question is:  How do I get Nautilus to display?  Is it something I need to install?

Again,
Thanks,
Dick


__________________

---

### Post by arnieboy on 2005-09-06
[QUOTE=kb7ypf]Hello arnieboy-

Back at again.  Your last e-mail in part said:
[B]gotcha. do the followin:
Code:

sudo mkdir /media/C: sudo gedit /etc/fstab


add the following line after the last line:
Quote:
/dev/hda1 /media/C: vfat umask=000 0 0

save and exit. reboot.
I dont think u care too much abt seeing the C: drive icon on ur desktop. but anytime u wanna access it, just go to /media/C: from nautilus or terminal and u will have read/write access to your C: drive.
EDIT: if u get a kick out of seeing the mounted drives on your desktop do the following:
go to System Tools--> Configurations Editor
and go to apps-->nautilus-->desktop and check volumes visible.[/B]

I followed your instructions and it worked.....Mucho Thanks

However my flavor of Ubuntu down not display "nautilus" under Apps.  I must be missing it.  I looked very hard for it, but it is not listed under any folder displayed under Applications. 

So the question is:  How do I get Nautilus to display?  Is it something I need to install?

Again,
Thanks,
Dick[/QUOTE]
Open up **System Tools-->Configuration editor** and in **Configuration Editor** go to  apps-->nautilus-->desktop and check volumes visible

---

### Post by kb7ypf on 2005-09-06
Got It  :) 

Thanks much for all your assistance.  

Everything is 100% working.

So Long Bill Gates  \\:D/ 



Dick

---

### Post by arnieboy on 2005-09-06
[QUOTE=kb7ypf]Got It  :) 

Thanks much for all your assistance.  

Everything is 100% working.

So Long Bill Gates  \\:D/ 



Dick[/QUOTE]
hey u are welcome :)

---

