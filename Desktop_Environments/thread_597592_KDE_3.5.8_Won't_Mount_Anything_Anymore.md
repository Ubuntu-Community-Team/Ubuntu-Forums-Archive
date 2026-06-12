---
title: "KDE 3.5.8 Won't Mount Anything Anymore"
date: 2007-10-30
forum: Desktop Environments
---

### Post by infidel on 2007-10-30
You know, on several occasions since October 18th, I've been *this* close to calling my upgrade to Gutsy "flawless". Perhaps I still can, as this appears to be a problem specific to KDE 3.5.8.

As of today, KDE won't mount anything at all. I put a CD or DVD in the drive, and nothing happens. Plug in my USB flashdrive-- nothing. It no longer sees my second (NTFS-formatted) hard drive. Nothing at all appears in system:/media. 

GNOME mounts everything normally. I get no dmesg or /var/log/messages output with regard to the optical drive when putting in a disc. Here's a tail -f of /var/log/messages for USB flashdrive insertion:

```
Oct 30 15:58:49 kane kernel: [ 9607.810226] usb 3-8: new high speed USB device using ehci_hcd and address 5
Oct 30 15:58:49 kane kernel: [ 9607.966289] usb 3-8: configuration #1 chosen from 1 choice
Oct 30 15:58:49 kane kernel: [ 9607.970205] scsi6 : SCSI emulation for USB Mass Storage devices
Oct 30 15:58:54 kane kernel: [ 9612.972282] scsi 6:0:0:0: Direct-Access              USB Flash Memory 1.00 PQ: 0 ANSI: 2
Oct 30 15:58:54 kane kernel: [ 9612.976382] sd 6:0:0:0: [sde] 1970176 512-byte hardware sectors (1009 MB)
Oct 30 15:58:54 kane kernel: [ 9612.977001] sd 6:0:0:0: [sde] Write Protect is off
Oct 30 15:58:54 kane kernel: [ 9612.980995] sd 6:0:0:0: [sde] 1970176 512-byte hardware sectors (1009 MB)
Oct 30 15:58:54 kane kernel: [ 9612.981621] sd 6:0:0:0: [sde] Write Protect is off
Oct 30 15:58:54 kane kernel: [ 9612.981630]  sde: sde1
Oct 30 15:58:54 kane kernel: [ 9612.982703] sd 6:0:0:0: [sde] Attached SCSI removable disk
Oct 30 15:58:54 kane kernel: [ 9612.982754] sd 6:0:0:0: Attached scsi generic sg4 type 0
```

It just doesn't end up mounted. The issue has survived restarts of KDE, as well as complete reboots.

Now, here's a twist: on one occasion, after inserting the USB flash drive, nothing happened. I opened System Places -> Storage Media, and saw nothing. Then, after perhaps a minute, the icon for the USB drive appeared in the unmounted state (I was able to mount it with a right-click). It was accompanied by a "mounted" icon for the NTFS drive. There was no accompanying notification/confirmation window, though, as there usually is when I plug in a USB device. I put a CD in the optical drive-- and it mounted and I got the "what would you like to do?" window. Afterward, things appear to be auto-mounting normally, but I can't say how long it will last.

Can anyone shed some light on this? I have made absolutely no changes to anything about my KDE installation in several days. Any and all guidance would be very much appreciated; thanks very much in advance.

---

### Post by taurus on 2007-10-30
Can you post

```
sudo fdisk -l
cat /etc/fstab
mount
```

---

### Post by infidel on 2007-10-30
> **taurus said:**
> Can you post

```
sudo fdisk -l
cat /etc/fstab
mount
```

I'm sorry; with or without stuff inserted? Or does it matter?

---

### Post by taurus on 2007-10-30
> **infidel said:**
> I'm sorry; with or without stuff inserted? Or does it matter?

With your external drives insert if you wish.  But first, we need to get your internal ntfs partition to mount.

---

### Post by infidel on 2007-10-30
> **taurus said:**
> With your external drives insert if you wish.  But first, we need to get your internal ntfs partition to mount.

Well, the NTFS drive is mounted now. Happened shortly after I opened the Storage Media flavor of Konqueror. Just appeared out of nowhere.

Here's fdisk -l:
```
Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x270b270a

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19796   159011338+  83  Linux
/dev/hda2           19797       19929     1068322+   5  Extended
/dev/hda5           19797       19929     1068291   82  Linux swap / Solaris

Disk /dev/hdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed67ed67

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *         581       20022   156167865    7  HPFS/NTFS
/dev/hdb2               1         580     4658818+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sde: 1008 MB, 1008730112 bytes
64 heads, 32 sectors/track, 962 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0xeeaedf5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1         962      984816    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(774, 63, 32) logical=(961, 47, 32)
```

Now, /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=aafc2e97-7b8e-4d5a-81a7-b553a56a744b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=d753fcf4-e0ca-485c-bc8b-eb4db5ca8ac6 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# Generated by Automatix
/dev/hdb2   /media/hdb2   vfat    iocharset=utf8,umask=000  0    0
/dev/hdb1   /media/hdb1   ntfs-3g  defaults,locale=en_US.utf8    0    0
## End of Automatix mounted partitions
```

(Yucky Automatix, I know... shame on me...)

And, mount:
```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/hdb2 on /media/hdb2 type vfat (rw,iocharset=utf8,umask=000)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sde1 on /media/disk type vfat (rw,nosuid,nodev,noatime,flush,uid=1000,utf8,shortname=lower)
```

As you can see, this was all done with the USB flashdrive inserted. Incidentally, it properly auto-mounted this time, with the notification window and everything.

---

### Post by taurus on 2007-10-30
So everything is now running good your end then.

---

### Post by infidel on 2007-10-30
It appears to be, though I'm at a loss to understand why it didn't for several hours, even despite reboots.

Is it just me, or is this release of KDE a bit twitchier than normal? My Adept Updater was screwy for several days, I'm still having occasional screensaver and monitor power management issues; now this (which may or may not be conclusively fixed). 

Anyway, thanks so much for your help. I'll post back here if it acts up again. ;)

---

