---
title: "mounting drive problem?"
date: 2009-02-25
forum: General Help
---

### Post by abhilashm86 on 2009-02-25
i am not able to mount my hard drives which are shown below,

abhilash@abhi:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff4bff4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/sda2            2433        9729    58613152+   f  W95 Ext'd (LBA)
/dev/sda5            2433        2476      343750   83  Linux
/dev/sda6            4866        7299    19542568+   b  W95 FAT32
/dev/sda7            7299        9729    19519888+   b  W95 FAT32
/dev/sda8            2477        4760    18346198+  83  Linux
/dev/sda9            4761        4865      843381   82  Linux swap / Solaris

i just  mounted my hard disk, i right clicked, there volume, then again on mount point i gave /media/SONGS (SONGS is name of my hard drive)

please help to recover:)

---

### Post by taurus on 2009-02-25
Are you trying to mount /dev/sda1, /dev/sda6, & /dev/sda7?

Post the outputs of these commands from a terminal.

```
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by abhilashm86 on 2009-02-25
yes you are right,i'm trying to mount 3 hard drives of 20 GB each, i was initially fed up of daily mounting hard disk,so i made changes then i suffered:)

ok now here are the results,

abhilash@abhi:~$ sudo blkid
/dev/sda1: UUID="3688CE2188CDDF8B" TYPE="ntfs" LABEL="WINDOWS XP" 
/dev/sda5: UUID="e18176ef-2ef4-4bcc-96ef-ebc8b9e2b922" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="SONGS" UUID="71B1-0D79" TYPE="vfat" 
/dev/sda7: LABEL="MUSIC" UUID="DCC5-0AE8" TYPE="vfat" 
/dev/sda8: UUID="67b2988e-eb79-445f-a7b2-25c061008e56" TYPE="ext3" 
/dev/sda9: TYPE="swap" UUID="53b39459-d52d-4d6a-bdb2-1e6bfcabfb36" 


abhilash@abhi:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=67b2988e-eb79-445f-a7b2-25c061008e56 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=53b39459-d52d-4d6a-bdb2-1e6bfcabfb36 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


abhilash@abhi:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              18G   11G  6.0G  64% /
varrun                502M  208K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   60K  502M   1% /dev
devshm                502M   12K  502M   1% /dev/shm
lrm                   502M   39M  463M   8% /lib/modules/2.6.24-23-generic/volatile
/dev/scd0             4.4G  4.4G     0 100% /media/cdrom0

---

### Post by taurus on 2009-02-25
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add the following three lines to the end of it.

```

UUID=3688CE2188CDDF8B   /media/windows   ntfs-3g   defaults,**locale=en_US**.UTF-8  0  0
UUID=71B1-0D79   /media/songs   vfat   iocharset=utf8,umask=000  0  0
UUID=DCC5-0AE8  /media/music   vfat   iocharset=utf8,umask=000 0  0

```
Replace **locale=en_US** for your **locale**, okay.  Then, save it and create three new mount points.

```
sudo mkdir /media/windows /media/songs /media/music
sudo mount -a
df -h
```
By the way, what happens to /dev/sda5 (ext3) since it's not mounted or in used at all?

---

### Post by abhilashm86 on 2009-02-25
> **taurus said:**
> Edit /etc/fstab

By the way, what happens to /dev/sda5 (ext3) since it's not mounted or in used at all?

hey that partition was created by ubuntu whaen i installed it, it shows lost+found directory and i can't even view things inside it, also i'm not able to format it, since its 200 mb i have left it:)

so do u have any idea why it got created/ it maybe my problem while installing?

---

### Post by abhilashm86 on 2009-02-25
/dev/sda5 2433 2476 343750 83 Linux
/dev/sda5: UUID="e18176ef-2ef4-4bcc-96ef-ebc8b9e2b922" SEC_TYPE="ext2" TYPE="ext3"

i get confused with above, why is both ext2 and ext3 is mentioned? also we can see linux there,so does every ubuntu user have one drive having "lost+found" thing?

what is meaning of above SEC_TYPE=ext2?

---

### Post by taurus on 2009-02-25
I guess you can unmount /dev/sd6 first.  Then, use gparted and delete /dev/sda5 and expand /dev/sda6 to take up that unallocated space if you wish.  Or you can just leave /dev/sda5 the way it is since it takes up 200MB.

The reason you see both ext2 and ext3 is because ext3 filesystem is backward compatible.  And every ext2 or ext3 filesystem has a lost+found directory in case it needs to "dump" some files to it during the recovery process after a system crash.

---

### Post by abhilashm86 on 2009-02-25
> **taurus said:**
>  
And every ext2 or ext3 filesystem has a lost+found directory in case it needs to "dump" some files to it during the recovery process after a system crash.

thanks for that info taurus:) yes thats what even i thought, ubuntu 8.04 has created a recovery in order at times of crash, i'll try expanding /dev/sda5 to other drive,anyways thanks again:)

---

### Post by Zimmer on 2009-02-25
you might be interested in the DISK MOUNTER applet that is available for the GNOME panel.... very handy...

---

### Post by abhilashm86 on 2009-02-25
> **Zimmer said:**
> you might be interested in the DISK MOUNTER applet that is available for the GNOME panel.... very handy...

ok how do u do that? i searched in synaptic,din't get and even i tried in terminal

abhilash@abhi:~$ sudo apt-get install DISK MOUNTER 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package DISK

tell how to get DISK MOUNTER?

---

### Post by Zimmer on 2009-02-26
install gnome-applets
Sorry about that, forgot about the extra package. Then Right click on the gnome panel ,click 
ADD TO PANEL 
and disk mounter should appear on the list .

Regards
Zimmer

---

### Post by abhilashm86 on 2009-02-26
> **Zimmer said:**
> install gnome-applets
Sorry about that, forgot about the extra package. Then Right click on the gnome panel ,click 
ADD TO PANEL 
and disk mounter should appear on the list .

Regards
Zimmer

hey thanks,cool one zimmer, i saw lot of applets now, i did install all like trash,media applet,wow its gr8...............

---

