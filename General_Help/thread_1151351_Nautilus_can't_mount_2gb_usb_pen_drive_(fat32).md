---
title: "Nautilus can't mount 2gb usb pen drive (fat32)"
date: 2009-05-06
forum: General Help
---

### Post by psychok9 on 2009-05-06
I've found a problem with Jaunty 9.04:
I can't mount with nautilus my 2gb pen drive usb (fat32 formatted).
I can do only with gparted or sudo mount etcetc (with root permission).

Solution?
I've tried to enable all permission on my user configuration (users settings).

---

### Post by salvachn on 2009-05-07
Reboot with the USD drive inserted, and then try.

---

### Post by colau on 2009-05-07
> **psychok9 said:**
> I've found a problem with Jaunty 9.04:
I can't mount with nautilus my 2gb pen drive usb (fat32 formatted).
I can do only with gparted or sudo mount etcetc (with root permission).

Solution?
I've tried to enable all permission on my user configuration (users settings).
Interesting.
I got no problem mounting 2GB pendrive.

---

### Post by psychok9 on 2009-05-07
In english the error is a little different:
[I]"Cannot mount volume.
Invalid mount option when attempting to mount the volume 'KING_2G'."[/I]

In my language is:
[I]"Cannot mount volume,
mount fs wrong, option not valid, superblock damaged or other error.
Try 'dmesg | tail'.[/I]

The pendrive work flawlessy, I can boot Ubuntu from it (and I've used it for last Ubuntu Jaunty installation).
I've see that gparted **mount my pendrive on /media/cdrom0**. It's normal?
It mount correctly the pendrive, but it's "root".

dmesg | tail:
```
[49014.744505] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[49014.744509]  sdd: sdd1
[49014.746146] sd 12:0:0:0: [sdd] Attached SCSI removable disk
[49014.746215] sd 12:0:0:0: Attached scsi generic sg5 type 0
[49015.114245] UDF-fs: No VRS found
[49015.166739] ISOFS: Unable to identify CD-ROM format.
[49024.479840] device-mapper: ioctl: unable to remove open device isw_daeghacjej_Raid2
[49032.448199] device-mapper: ioctl: unable to remove open device isw_daeghacjej_Raid2
[49063.564869] device-mapper: ioctl: unable to remove open device isw_daeghacjej_Raid2
[49103.205179] usb 2-2: USB disconnect, address 7
```

---

### Post by mc4man on 2009-05-07
Check your fstab, if you installed from the pendrive then it's likely listed as a cdrom drive
If so, then comment out or delete the entry

it would look something like this (not sure about the red, should be obvious though
/dev/[COLOR="Red"]sdd1[/COLOR]       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0

---

### Post by psychok9 on 2009-05-07
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/mapper/isw_daeghacjej_Raid2 during installation
UUID=003c37ff-66e8-4a20-b2f5-5cca0f4164af /               ext4    relatime,errors=remount-ro 0       1
# /media/BackLinux was on /dev/sda2 during installation
UUID=eb612073-b169-426c-be88-384408c23092 /media/BackLinux ext3    relatime        0       2
# /media/BackWin was on /dev/sda3 during installation
UUID=0146D7D64ACDA4A6 /media/BackWin  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
```

Only now... I've see it!!! -> /dev/sdd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
Thank you!

---

### Post by psychok9 on 2009-05-07
Commented out, reboot and solved! :guitar:

---

