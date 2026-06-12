---
title: "CD/DVD not mounting in Xubuntu Hardy"
date: 2008-07-20
forum: Desktop Environments
---

### Post by Melcar on 2008-07-20
My optical drive is detected when I do lshw, and I know it works.  Problem is it does not mount when I insert any type of media.  I already checked all the options under the "Removable drives and media" menu, but still the drive does not mount.  When I try to mount it manually I get:

```
javier@scrapbox:~$ sudo mount /dev/hdb
mount: block device /dev/hdb is write-protected, mounting read-only
javier@scrapbox:~$ 
```

... but nothing happens.

---

### Post by tech0007 on 2008-07-20
Post your /etc/fstab and 'tail /var/log/syslog' right after you mount hdb. I suppose hardy uses /dev/sdX's now.

---

### Post by Melcar on 2008-07-20
```
javier@scrapbox:~$ sudo tail /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=6bd4ce92-ed0e-499e-8f54-663003d16da9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=d888a992-537c-4893-b44d-c8f6f7cadec5 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

```
javier@scrapbox:~$ sudo tail /var/log/syslog
Jul 20 17:36:41 scrapbox kernel: [ 3014.802599] [drm] Num pipes: 2
Jul 20 17:36:53 scrapbox kernel: [ 3026.891492] [drm] Num pipes: 2
Jul 20 17:36:53 scrapbox kernel: [ 3027.155994] [drm] Num pipes: 2
Jul 20 17:37:01 scrapbox kernel: [ 3034.762983] [drm] Num pipes: 2
Jul 20 17:37:24 scrapbox kernel: [ 3057.707049] [drm] Num pipes: 2
Jul 20 17:37:36 scrapbox kernel: [ 3070.228756] [drm] Num pipes: 2
Jul 20 17:39:02 scrapbox /USR/SBIN/CRON[7790]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jul 20 17:47:44 scrapbox kernel: [ 3678.480179] UDF-fs: No VRS found
Jul 20 17:47:44 scrapbox kernel: [ 3678.624009] ISO 9660 Extensions: Microsoft Joliet Level 3
Jul 20 17:47:45 scrapbox kernel: [ 3678.701875] ISO 9660 Extensions: RRIP_1991A

```

```

javier@scrapbox:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: SAMSUNG SP0411N
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: TW100-11
       serial: S01JJ50XB21202
       size: 37GiB (40GB)
       capacity: 37GiB (40GB)
       capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
       configuration: signature=e06fe06f smart=on
  *-cdrom
       description: DVD writer
       product: _NEC DVD_RW ND-3520A
       physical id: 1
       bus info: ide@0.1
       logical name: /dev/hdb
       logical name: /media/cdrom0
       version: 1.04
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
       configuration: mode=udma2 mount.fstype=iso9660 mount.options=ro,nosuid,nodev state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/hdb
          logical name: /media/cdrom0
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev state=mounted

```
The weird thing is that all other forms of media (USB keys, external HDDs) mount automatically with no problems.

---

### Post by sisco311 on 2008-07-20
> **tech0007 said:**
> Post your /etc/fstab and 'tail /var/log/syslog' right after you mount hdb. I suppose hardy uses /dev/sdX's now.
I think hardy uses /dev/sdX for external devices
and /dev/scdY, /dev/srY, /dev/dvd,  /dev/cdrom for internal optical devices 
OP: also post:
```
lshw -C disk
```

---

### Post by sisco311 on 2008-07-20
according to the logs the cd/dvd is mounted
```
thunar /media/cdrom0
```
still nothing?

---

### Post by Melcar on 2008-07-20
> **sisco311 said:**
> according to the logs the cd/dvd is mounted
```
thunar /media/cdrom0
```
still nothing?

It's shows that it's mounted because I did it manually.  It mounts fine and I can browse the disk by way of Thunar just fine (thought the icon does not appear on my desktop), the problem is that I have to mount the drive while normally it happens automatically (GNOME and KDE do it, so does the previous releases of XFCE).  This also means that DVDs will not start automatically either; I have to also mount the drive manually and launch the movie.

---

### Post by sisco311 on 2008-07-20
i've (temporarily)switched from xfce to openbox
and i have the same problem.
i thought it's openbox related.
looks like it's not.
it's 4:20am here.

i will investigate this tomorrow.
(you don't need to mount the drive as root (the *user* option in fstab allows users to mount the drive))

---

### Post by sisco311 on 2008-07-21
In xubuntu the default volume-manager is thunar-volman.
Make sure it's configured correctly:[http://thunar.xfce.org/documentation/C/using-removable-media.html#management-of-removable-drives-and-media](http://thunar.xfce.org/documentation/C/using-removable-media.html#management-of-removable-drives-and-media)

(i'm using now ivman with openbox, works=D>)

---

### Post by Melcar on 2008-07-22
Volume management is on.  Everything else auto mounts normally (USB sticks, external HDDs, etc), just anything that I put on my optical drive doesn't.
By the way, while searching for an answer I kept seeing references to HAL.  HAL does hang for an uncanny amount of time when the machine boots up.

---

### Post by sparkstealer on 2008-10-08
Hello.  Sorry to be posting on an old thread, but I noticed this thread is not closed, and I don't think my problem is different enough to warrant a new thread.

However, when I try to mount my CD/DVD ROM, I get this:
```

castleart@Samantha:~$ sudo mount /dev/hdc
mount: special device /dev/hdc does not exist
castleart@Samantha:~$ 

```

I tried going through the steps listed here already.  tail /etc/fstab shows this:
```

castleart@Samantha:~$ sudo tail /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=a89aa0ec-a5a9-4435-9358-fe8cea2d0a73 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=cc0d5f49-e711-4970-a037-2495c4010412 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

tail /var/log/syslog shows (this is after I verified a data disc would work fine and with an audio CD in the drive):
```

Oct  8 20:09:12 Samantha kernel: [ 4853.916903] end_request: I/O error, dev sr0, sector 0
Oct  8 20:13:21 Samantha NetworkManager: <debug> [1223511201.512504] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_612945920'). 
Oct  8 20:14:04 Samantha NetworkManager: <debug> [1223511244.945033] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Gaming___Jul08'). 
Oct  8 20:14:08 Samantha kernel: [ 5150.248717] ISO 9660 Extensions: Microsoft Joliet Level 3
Oct  8 20:14:11 Samantha kernel: [ 5153.212788] ISOFS: changing to secondary root
Oct  8 20:14:11 Samantha hald: mounted /dev/scd0 on behalf of uid 1000
Oct  8 20:17:01 Samantha /USR/SBIN/CRON[5193]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  8 20:28:16 Samantha hald: unmounted /dev/scd0 from '/media/Gaming - Jul08' on behalf of uid 1000
Oct  8 20:28:19 Samantha NetworkManager: <debug> [1223512099.892736] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_label_Gaming___Jul08'). 
Oct  8 20:28:54 Samantha NetworkManager: <debug> [1223512134.197138] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_612945920'). 

```

lshw -C disk gets me:
```

castleart@Samantha:~$ sudo lshw -C disk
  *-disk:0                
       description: ATA Disk
       product: WDC WD102AA
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 05.0
       serial: WD-WMA0M1797715
       size: 9787MiB (10GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00012fb6
  *-cdrom
       description: DVD reader
       product: DVD-ROM DVD-114
       vendor: PIONEER
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.17
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
  *-disk:1
       description: SCSI Disk
       product: ZIP 100
       vendor: IOMEGA
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/sdb
       version: 03.H
       capabilities: removable
       configuration: ansiversion=5
     *-medium
          physical id: 0
          logical name: /dev/sdb

```

And Thunar does not show the drive at all, even with a disc in the drive.  However, when I insert a disc, it triggers the default player program to open.  Also, data discs mount just fine.

---

