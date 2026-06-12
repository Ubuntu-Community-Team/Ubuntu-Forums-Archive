---
title: "drives mounting as root."
date: 2009-04-08
forum: Desktop Environments
---

### Post by leona on 2009-04-08
Hi There

I do not know if this is expected behavour, but I have recently been having trouble with external drives, usb sticks, FAT32 drives etc.

Basically it keeps telling me I don't have permission to access them, when I look at the directories in /media they are all 'root' as user and group, why is this? is it right? if not, how do I correct it?  I need everyone to be able to access these drives.  I don't know why it worked one day then didn't the next, I don't understand why things change without me doing anything.

The drives are ok, if I load a terminal window and log in as root I can access them fine, so all the data and drives are ok, but no users can see them.

```

32 drwx------ 38 root root 32768 1970-01-01 01:00 DATA
 4 drwxr-xr-x  2 root root  4096 2008-05-26 16:13 cdrom0
 0 lrwxrwxrwx  1 root root     6 2008-05-26 16:13 cdrom -> cdrom0
 4 drwxr-xr-x  2 root  999  4096 2008-05-26 16:13 floppy0
 0 lrwxrwxrwx  1 root  999     7 2008-05-26 16:13 floppy -> floppy0
 4 drwx------  2 root root  4096 2008-06-02 07:57 SD2GIG
 4 drwxrwxrwx  8 root root  4096 2009-04-02 17:48 disk

```

As you can see 'DATA' (FAT32 Partition) & SD2GIG (pen drive) is only accessible by root, had the same problem with 'disk' (removable hard drive) so I 'fudged' that with su root chmod 777 disk, but that isn't working for 'DATA' and I don't know why, I am sure I am not supposed to do it like this, but I know no other way to fix the problem.

I need to ensure that any connected to my machine is viewable by all users, having it stuck to root is of no use to me.

Thank you

Leona.

---

### Post by taurus on 2009-04-08
Can you remount it from a terminal, _assuming_ it is /dev/sda2?

```
sudo umount /media/DATA
sudo mount -t vfat /dev/sda2 /media/DATA -o umask=000
ls -la /media
```

---

### Post by leona on 2009-04-08
Thank you taurus, that did work, will this remain or will I have to run this every time I log on?
Will i have to do this each time I plug a new device in?

---

### Post by taurus on 2009-04-08
Do you have an entry to mount that partition, whichever that is, to /media/DATA in /etc/fstab?

```
cat /etc/fstab
```

---

### Post by leona on 2009-04-16
Hi taurus, interesting, there is no entry in fstab for these drives, can one be added?
Just looking at it, how do I work out what 'dev' it is?

---

### Post by taurus on 2009-04-16
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda2   /media/DATA   vfat  iocharset=utf8,umask=000  0  0
```
Save it and reboot.  Now, see if /dev/sda2 is really mounted to /media/DATA.

```
ls -la /media/DATA
```
And if you're not sure which device it is, post the outputs of these commands.

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by leona on 2009-04-21
Thanks taurus

Outputs from the commands are as follows.

```

sudo fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd9a5d9a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    c  W95 FAT32 (LBA)
/dev/sda2            1276       19457   146046915    f  W95 Ext'd (LBA)
/dev/sda5            1276        8855    60886318+   b  W95 FAT32
/dev/sda6            8856       11915    24579418+   b  W95 FAT32
/dev/sda7           11916       12049     1076323+  83  Linux
/dev/sda8           12050       14017    15807928+  83  Linux
/dev/sda9           14018       18912    39319056   83  Linux
/dev/sda10          18913       19457     4377681   82  Linux swap / Solaris

```

```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=89a24bda-e31b-4205-a711-d95170b5eff8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=0e672aef-12b9-44ed-ac27-bf9b6f9bf0ab /boot           ext3    relatime        0       2
# /dev/sda9
UUID=0a19f1ca-c309-4a0f-adbc-74b216ea839a /home           ext3    relatime        0       2
# /dev/sda10
UUID=7f891555-ff67-4138-904a-8c275340851f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


```

```

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              15G  4.7G  9.6G  33% /
varrun               1007M  228K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
procbususb           1007M   80K 1007M   1% /proc/bus/usb
udev                 1007M   80K 1007M   1% /dev
devshm               1007M  116K 1007M   1% /dev/shm
lrm                  1007M   44M  963M   5% /lib/modules/2.6.24-23-generic/volatile
/dev/sda7             1.1G  162M  829M  17% /boot
/dev/sda9              37G   26G   12G  69% /home
gvfs-fuse-daemon       15G  4.7G  9.6G  33% /home/leona/.gvfs

```

Looks like /dev/sda5 is the one I need, is that right?

Thanks.

---

