---
title: "Swap Partition will not mount"
date: 2009-01-29
forum: General Help
---

### Post by lsutiger on 2009-01-29
Here is fdisk -l:
```
brian@brian-linux:~$ sudo fdisk -l

Disk /dev/sdc: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0fac0fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1219     9791586   83  Linux
/dev/sdc2            1220        9606    67368577+  83  Linux
/dev/sdc3            9607        9730      996030   82  Linux swap / Solaris

Disk /dev/sdd: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc5cbc5cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        2028    16289878+   7  HPFS/NTFS
/dev/sdd2            2551        9038    52114860    f  W95 Ext'd (LBA)
[COLOR="Red"]/dev/sdd3            2029        2550     4192965   82  Linux swap / Solaris[/COLOR]
/dev/sdd5            2551        9038    52114828+   7  HPFS/NTFS

Partition table entries are not in disk order

```

Here is fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8d262e5f-7be5-498e-8fb6-ff8e8500eb07 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=db94cdec-be1f-415b-a6da-6cde9319de27 /home           ext3    defaults        0       2
# /dev/sda3
UUID=0ffb86ab-e791-4a12-884f-bc09846a237a none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
none /proc/bus/usb usbfs devgid=120,devmode=664 0 0
//SERVER/brian /mnt/brian cifs credentials=/home/brian/.smbcredentials,uid=1000 0 0
//SERVER/LogFiles /mnt/logs cifs credentials=/home/brian/.smbcredentials,uid=1000 0 0
//SERVER/tfalgout /mnt/pnl cifs credentials=/home/brian/.smbcredentials,uid=1000 0 0
//SERVER/ftp /mnt/ftp cifs credentials=/home/brian/.smbcredentials,uid=1000 0 0
//SERVER/Inetpub /mnt/mail cifs credentials=/home/brian/.smbcredentials,uid=1000 0 0
//SERVER/www /mnt/www cifs credentials=/home/brian/.smbcredentials,uid=1000 0 0
# /dev/sdc5
/dev/sdd5 /mnt/disk2 ntfs-3g defaults 0 0 
[COLOR="Red"]/dev/sdd3 swap swap defaults 0 0[/COLOR]
```

after sudo mount -a I get no errors. 

free :
```
brian@brian-linux:~$ free
             total       used       free     shared    buffers     cached
Mem:       2075492    1995072      80420          0      12048     231172
-/+ buffers/cache:    1751852     323640
Swap:            0          0          0

```

Whats up with this?

---

### Post by uidb4056 on 2009-01-29
In the last line of your fstab you have duplicated your swap definition given also bad mountpoint, i would recommend you delete this line and verify if the output of the command 'sudo blkid' matches the UUID showed for /dev/sda3 with what you have in your fstab

---

### Post by damis648 on 2009-01-29
Open a terminal and try:
```
sudo swapon /dev/sdd3
```
and let us know what happens.

EDIT: Yes, also remove the very last line of your fstab, you declared swap twice.

---

### Post by caljohnsmith on 2009-01-29
Looks like the swap line in your fstab is slightly off, how about trying instead:
```
/dev/sdd3 none            swap    sw   0 0
```
Let me know if that works or not.

---

### Post by damis648 on 2009-01-29
> **caljohnsmith said:**
> Looks like the swap line in your fstab is slightly off, how about trying instead:
```
/dev/sdd3 none            swap    sw   0 0
```
Let me know if that works or not.

Swap is in there twice. I recommend you try this fstab and see how it goes:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8d262e5f-7be5-498e-8fb6-ff8e8500eb07 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=db94cdec-be1f-415b-a6da-6cde9319de27 /home           ext3    defaults        0       2
# /dev/sda3
/dev/sdd3 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
none /proc/bus/usb usbfs devgid=120,devmode=664 0 0
//SERVER/brian /mnt/brian cifs credentials=/home/brian/.smbcredentials,uid=1000 0 0
//SERVER/LogFiles /mnt/logs cifs credentials=/home/brian/.smbcredentials,uid=1000 0 0
//SERVER/tfalgout /mnt/pnl cifs credentials=/home/brian/.smbcredentials,uid=1000 0 0
//SERVER/ftp /mnt/ftp cifs credentials=/home/brian/.smbcredentials,uid=1000 0 0
//SERVER/Inetpub /mnt/mail cifs credentials=/home/brian/.smbcredentials,uid=1000 0 0
//SERVER/www /mnt/www cifs credentials=/home/brian/.smbcredentials,uid=1000 0 0
# /dev/sdc5
/dev/sdd5 /mnt/disk2 ntfs-3g defaults 0 0 
```

I removed the last line and fixed the swap line to not refer to it by the UUID but instead by the block device.

---

### Post by lsutiger on 2009-01-29
OK..did not recognize that. Output from  ls -l /dev/disk/by-uui
```
brian@brian-linux:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-01-28 12:05 48EA-7C98 -> ../../sdd1
lrwxrwxrwx 1 root root 10 2009-01-28 12:05 8d262e5f-7be5-498e-8fb6-ff8e8500eb07 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2009-01-28 12:05 [COLOR="Red"]a8c43e2b-e9ea-4336-b015-e7c5af14b957[/COLOR] -> ../../sdc3
lrwxrwxrwx 1 root root 10 2009-01-28 12:05 C400D60C00D60578 -> ../../sdd5
lrwxrwxrwx 1 root root 10 2009-01-28 12:05 db94cdec-be1f-415b-a6da-6cde9319de27 -> ../../sdc2
lrwxrwxrwx 1 root root 10 2009-01-28 12:05 e21fda3b-c394-422f-94ea-3efeeb1a53aa -> ../../sdd3

```

New fstab:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8d262e5f-7be5-498e-8fb6-ff8e8500eb07 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=db94cdec-be1f-415b-a6da-6cde9319de27 /home           ext3    defaults        0       2
# /dev/sda3
UUID=[COLOR="Red"]a8c43e2b-e9ea-4336-b015-e7c5af14b957[/COLOR] none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
none /proc/bus/usb usbfs devgid=120,devmode=664 0 0
//SERVER/brian /mnt/brian cifs credentials=/home/brian/.smbcredentials,uid=1000 0 0
//SERVER/LogFiles /mnt/logs cifs credentials=/home/brian/.smbcredentials,uid=1000 0 0
//SERVER/tfalgout /mnt/pnl cifs credentials=/home/brian/.smbcredentials,uid=1000 0 0
//SERVER/ftp /mnt/ftp cifs credentials=/home/brian/.smbcredentials,uid=1000 0 0
//SERVER/Inetpub /mnt/mail cifs credentials=/home/brian/.smbcredentials,uid=1000 0 0
//SERVER/www /mnt/www cifs credentials=/home/brian/.smbcredentials,uid=1000 0 0
# /dev/sdc5
/dev/sdd5 /mnt/disk2 ntfs-3g defaults 0 0 

```

output of sudo blkid:
```
brian@brian-linux:~$ sudo blkid
/dev/sdc1: UUID="8d262e5f-7be5-498e-8fb6-ff8e8500eb07" TYPE="ext3" 
/dev/sdc3: TYPE="swap" UUID="a8c43e2b-e9ea-4336-b015-e7c5af14b957" 
/dev/sdd1: UUID="48EA-7C98" TYPE="vfat" 
/dev/sdd5: UUID="C400D60C00D60578" TYPE="ntfs" 
/dev/sdc2: UUID="db94cdec-be1f-415b-a6da-6cde9319de27" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd3: TYPE="swap" UUID="e21fda3b-c394-422f-94ea-3efeeb1a53aa" 

```

They match now but I still get:
```
brian@brian-linux:~$ free
             total       used       free     shared    buffers     cached
Mem:       2075492    2017992      57500          0       4348     128820
-/+ buffers/cache:    1884824     190668
Swap:            0          0          0

```

---

### Post by Yashiro on 2009-01-29
Try setting swap on the partition using *gparted*.

---

### Post by caljohnsmith on 2009-01-29
> **lsutiger said:**
> 
output of sudo blkid:
```
brian@brian-linux:~$ sudo blkid
/dev/sdc1: UUID="8d262e5f-7be5-498e-8fb6-ff8e8500eb07" TYPE="ext3" 
/dev/sdc3: TYPE="swap" UUID="a8c43e2b-e9ea-4336-b015-e7c5af14b957" 
/dev/sdd1: UUID="48EA-7C98" TYPE="vfat" 
/dev/sdd5: UUID="C400D60C00D60578" TYPE="ntfs" 
/dev/sdc2: UUID="db94cdec-be1f-415b-a6da-6cde9319de27" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd3: TYPE="swap" UUID=[COLOR="Red"]"e21fda3b-c394-422f-94ea-3efeeb1a53aa"[/COLOR] 

```

It doesn't look like the swap UUID of blkid matches your fstab. When you boot, have you noticed losing the Ubuntu splash screen? If so, please don't change your fstab to use the new swap UUID, how about first posting:
```
cat /etc/initramfs-tools/conf.d/resume
```

---

### Post by damis648 on 2009-01-29
> **caljohnsmith said:**
> It doesn't look like the swap UUID of blkid matches your fstab. When you boot, have you noticed losing the Ubuntu splash screen? If so, please don't change your fstab to use the new swap UUID, how about first posting:
```
cat /etc/initramfs-tools/conf.d/resume
```

That used to happen to me alot. Look into that. But also make sure to try
```
sudo swapon /dev/sdd3
```

---

### Post by caljohnsmith on 2009-01-29
**Lsutige**, is the idea that you want to use two swap partitions? If so, how about changing your fstab to use the following two swap entries (the first one you all ready have, but the second entry you would need to add):
```

UUID=a8c43e2b-e9ea-4336-b015-e7c5af14b957 none   swap    sw   0  0
UUID=e21fda3b-c394-422f-94ea-3efeeb1a53aa none   swap    sw   0  0
```

---

### Post by lsutiger on 2009-01-29
Whew! A lot of replies!! Thanx a bunch!

This started after I updated a lot of different things yesterday. While running multiple spreadsheets in open office (which I do often!), my system came to a near halt. So I ran free and noticed no swap....so I have no idea how this came to be.

Here are some replies:
```
brian@brian-linux:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=0ffb86ab-e791-4a12-884f-bc09846a237a

```

```
brian@brian-linux:~$ sudo swapon /dev/sdd3
[sudo] password for brian: 
brian@brian-linux:~$ free
             total       used       free     shared    buffers     cached
Mem:       2075492    2021348      54144          0       3168     194936
-/+ buffers/cache:    1823244     252248
Swap:      4192956          0    4192956

```


so I got my swap back with that. But what should I do with the fstab??

No, not looking for 2 swap partitions. I just ended up with 2...I had a large open spot on one of my drives, so I created a swap partition  and switched it to that quite a few months ago.

---

### Post by caljohnsmith on 2009-01-29
So is it the sdd3 swap partition you want to use I assume, not the sdc3 swap partition? If so, how about doing:
```
sudo swapoff -a
sudo mkswap -U $(awk -F= '{print $3}' /etc/initramfs-tools/conf.d/resume) /dev/sdd3
```
And then change your fstab to also use the same UUID in your resume file:
```
UUID=0ffb86ab-e791-4a12-884f-bc09846a237a  none   swap    sw   0  0
```
Reboot, and then check that you have swap with:
```
free
```
And let us know how it goes.

---

### Post by lsutiger on 2009-01-29
Will do! This is my work computer, which I need up and running during business hours, and today has been a very long day. I will do so about lunch time. 

I gotta get out of here :)
thanx for all of the replies!

---

### Post by lsutiger on 2009-01-30
Question...what is this:

cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=0ffb86ab-e791-4a12-884f-bc09846a237a

---

### Post by caljohnsmith on 2009-01-30
> **lsutiger said:**
> Question...what is this:

cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=0ffb86ab-e791-4a12-884f-bc09846a237a
If I remember correctly, I believe that file tells Ubuntu which file/partition to use for storing the hibernation data when you hibernate your computer. Although you may not use hibernation, if the file/partition listed in the resume file is not found on start up, one of the symptoms is that you will lose your Ubuntu splash screen.

---

