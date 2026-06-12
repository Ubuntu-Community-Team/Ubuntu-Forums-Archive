---
title: "usb flashdrives/eSata drives mount only with sudo"
date: 2009-03-31
forum: General Help
---

### Post by Don Giovanni on 2009-03-31
I can no longer mount usb flash drives, or my eSata drives as my user

the only way to mount them is using sudo
```

sudo mount /dev/sdc /media/eSata

```
works but if i try it without sudo, or try to mount the drive from the places menu/nautilus it will not mount.



This is likely something self inflicted.  Recently I decided to get rid of my windows partion and also change over my linux install to JFS.  I tar'd up my linux install with
```

tar cvpzf /media/eSataII/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/media --exclude=/sys /

```
Booted with a live CD, repartitioned & formated the primary drive, unpacked the tar (from my eSata drive) fixed up grub and fstab with new uuid for partition, recreated the /proc /lost+found /mnt /media and /sys folders and rebooted.

Upon reboot I had the issue with not being able to mount any usb or esata device (they work fine in other machines).
dmesg | tail and cat /var/log/messages | tail
don't seem to show any errors when i insert the device.

dmesg | tail
```

[ 1609.840904] sd 8:0:0:0: [sde] Write Protect is off
[ 1609.840907] sd 8:0:0:0: [sde] Mode Sense: 03 00 00 00
[ 1609.840908] sd 8:0:0:0: [sde] Assuming drive cache: write through
[ 1609.842995] sd 8:0:0:0: [sde] 3970048 512-byte hardware sectors (2033 MB)
[ 1609.845008] sd 8:0:0:0: [sde] Write Protect is off
[ 1609.845012] sd 8:0:0:0: [sde] Mode Sense: 03 00 00 00
[ 1609.845014] sd 8:0:0:0: [sde] Assuming drive cache: write through
[ 1609.845018]  sde: sde1
[ 1609.848977] sd 8:0:0:0: [sde] Attached SCSI removable disk
[ 1609.849072] sd 8:0:0:0: Attached scsi generic sg5 type 0

```

cat /var/log/messages | tail
```

Mar 30 23:05:22 maximus-l kernel: [ 1604.834958] usb 4-1: configuration #1 chosen from 1 choice
Mar 30 23:05:22 maximus-l kernel: [ 1604.835504] scsi8 : SCSI emulation for USB Mass Storage devices
Mar 30 23:05:27 maximus-l kernel: [ 1609.838416] scsi 8:0:0:0: Direct-Access     USB 2.0  SD/MMC Reader         PQ: 0 ANSI: 0 CCS
Mar 30 23:05:27 maximus-l kernel: [ 1609.840407] sd 8:0:0:0: [sde] 3970048 512-byte hardware sectors (2033 MB)
Mar 30 23:05:27 maximus-l kernel: [ 1609.840904] sd 8:0:0:0: [sde] Write Protect is off
Mar 30 23:05:27 maximus-l kernel: [ 1609.842995] sd 8:0:0:0: [sde] 3970048 512-byte hardware sectors (2033 MB)
Mar 30 23:05:27 maximus-l kernel: [ 1609.845008] sd 8:0:0:0: [sde] Write Protect is off
Mar 30 23:05:27 maximus-l kernel: [ 1609.845018]  sde: sde1
Mar 30 23:05:27 maximus-l kernel: [ 1609.848977] sd 8:0:0:0: [sde] Attached SCSI removable disk
Mar 30 23:05:27 maximus-l kernel: [ 1609.849072] sd 8:0:0:0: Attached scsi generic sg5 type 0

```

---

### Post by Don Giovanni on 2009-03-31
In another thread it was advised to
System->Administration->Users and Groups
then select your user and hit properties. Make sure "Access external storage devices automatically"

It appears that is broken as well. Are the two related?

Clicking Users and Groups gives me "The configuration could not be loaded.  You are not allowed to access the system configuration."

I was able to previously.

---

### Post by kngunn on 2009-04-23
Similiar problem for me, it only applies to eSATA.  USB works fine.

To mount an eSATA drive requires 

   sudo mount /dev/sdc1 /media/mountpoint

Anyone else found a decent solution?

---

### Post by toopi on 2009-04-25
```
 gksu polkit-gnome-authorization 
```

Refer to the attached screenshot.
- Click on "Edit" under "Implicit Authorizations"
- Make note of the original settings
- Play around with the options

However, I cannot really tell how it would affect the security aspects of your machine.

---

