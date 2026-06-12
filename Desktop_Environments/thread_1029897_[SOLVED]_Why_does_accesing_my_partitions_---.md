---
title: "[SOLVED] Why does accesing my partitions ---"
date: 2009-01-03
forum: Desktop Environments
---

### Post by tropdoug on 2009-01-03
result in me asked for my password? 

I have recently switched to trying KDE 4.1 and I actually like it, there are some puzzling aspects though, one of which is the above issue. My main drive is split into three partitions, and whenever I want to access either my music one, or my business data, I get asked for my password. It only takes a second to put in, but it's an annoying inconveniance. 

How do I stop it, and why is this the default?

Thanks

---

### Post by taurus on 2009-01-03
Are music and business on separate partitions?

---

### Post by tropdoug on 2009-01-03
Yes they are

---

### Post by taurus on 2009-01-03
Can you post the outputs of these commands?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```
Which partition is music and which partition is business?

---

### Post by tropdoug on 2009-01-04
Here goes

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4eab4176                     

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3888    31230328+  83  Linux
/dev/sda2            3889        6797    23366542+  83  Linux
/dev/sda3            6798        9729    23551290    5  Extended
/dev/sda5            6798        9602    22531131   83  Linux
/dev/sda6            9603        9729     1020096   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3657373

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x170a8ae2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    c  W95 FAT32 (LBA)

Disk /dev/sdd: 2062 MB, 2062548992 bytes
16 heads, 32 sectors/track, 7868 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x6b6f5d80
[FONT=monospace]douglas@douglas-desktop:~$[/FONT]

```sda1 = Root 
sda2 = Business
sda 5 = Music

My /home partition is on a separate 80 gig internal drive sdb1 mounted from fstab


```
douglas@douglas-desktop:~$ sudo blkid
/dev/sda1: UUID="c01c0de0-08ff-4fd3-8bc2-9666ce46d92f" TYPE="ext3"
/dev/sda2: LABEL="Business" UUID="d5790e2d-6871-4dea-ba09-ba1ee7029fbc" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: LABEL="MyMusic" UUID="74cc19ce-abc2-4383-abd7-31bc0030639f" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda6: TYPE="swap" UUID="9dc92dc0-2b3b-410a-95e7-ad6273399e4a"
/dev/sdb1: UUID="4948316e-a1dc-45f4-8e24-f4872f6695af" TYPE="ext3"
/dev/sdc1: LABEL="seagate" UUID="8ae7ccdc-69be-4bef-a3af-f3f07ab45c50" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdd1: SEC_TYPE="msdos" LABEL="NANO" UUID="BC55-1160" TYPE="vfat"
douglas@douglas-desktop:~$

```Disregard sdc1 & sdd1 they just happen to be a usb stick and an external drive I have working as I did this

```
douglas@douglas-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c01c0de0-08ff-4fd3-8bc2-9666ce46d92f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=4948316e-a1dc-45f4-8e24-f4872f6695af /home           ext3    relatime        0       2
# /dev/sda6
UUID=9dc92dc0-2b3b-410a-95e7-ad6273399e4a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none  /proc/bus/usb  usbfs  devgid=46,devmode=664  0  0

``````
douglas@douglas-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              30G  4.6G   24G  17% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  104K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.9M  498M   1% /dev
tmpfs                 501M     0  501M   0% /dev/shm
lrm                   501M  2.4M  499M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb1              74G  4.0G   66G   6% /home
/dev/sda5              22G   16G  4.8G  77% /media/MyMusic
/dev/sda2              22G   20G  1.9G  92% /media/Business
douglas@douglas-desktop:~$

```What is the df -h telling me? I know the other two. 

Thanks for this help

---

### Post by taurus on 2009-01-04
Why not add two entries in /etc/fstab for /dev/sda2 & /dev/sda5 so they would be mounted automatically each time you boot Ubuntu.  

First, unmount them.

```
sudo umount /media/MyMusic /media/Business
```

Then, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```

UUID=74cc19ce-abc2-4383-abd7-31bc0030639f    /media/MyMusic   ext3   defaults   0   2
UUID=d5790e2d-6871-4dea-ba09-ba1ee7029fbc   /media/Business   ext3   defaults   0   2

```

Save it and close gedit editing window.  Now, create those mount points (if they don't exist) and mount them.

```
sudo mkdir /media/MyMusic
sudo mkdir /media/Business
sudo mount -a
df -h
```
Then, just change the ownership of those two mount points from root to your login name, douglas.

```
sudo chown -R douglas:douglas /media/MyMusic
sudo chown -R douglas:douglas /media/Business
ls -la /media
```

---

### Post by tropdoug on 2009-01-05
Thanks very much Taurus, you are a good teacher. Not only have you solved the issue for me, but I have a much better understanding of the mount process, the way fstab works, and how to get the necessary information to avoid blind mistakes. I hope that one day I too will be able to help someone as well. 

Again thanks and maybe others will find this thread useful too. 

Doug

---

