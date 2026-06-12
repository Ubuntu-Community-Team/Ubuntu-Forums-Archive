---
title: "Ubuntu 7.10: Cannot mount USB"
date: 2007-10-20
forum: Desktop Environments
---

### Post by backon18 on 2007-10-20
Just installed Ubuntu 7.10 on my X61. Everything seems to be working. Love the system. But one serious problem: I cannot mount usb! Help please!

After I plugged my usb memory key, the system tried to mount but failed. It said: Cannot mount volumn. invalid mount option when attemping to mount the volume 'TRAVELDRIVE'.

dmesg showed:
[ 386.388000] UDF-fs: No partition found (1)
[ 386.432000] Unable to identify CD-ROM format.
[ 465.116000] UDF-fs: No partition found (1)
[ 465.156000] Unable to identify CD-ROM format.
[ 492.632000] UDF-fs: No partition found (1)
[ 492.676000] Unable to identify CD-ROM format.
[ 533.748000] UDF-fs: No partition found (1)
[ 533.792000] Unable to identify CD-ROM format.
[ 592.784000] usb 6-2: USB disconnect, address 2
[ 598.296000] usb 6-2: new high speed USB device using ehci_hcd and address3
[ 598.432000] usb 6-2: configuration #1 chosen from 1 choice
[ 598.432000] scsi5 : SCSI emulation for USB Mass Storage devices
[ 598.432000] usb-storage: device found at 3
[ 598.432000] usb-storage: waiting for device to settle before scanning
[ 603.432000] usb-storage: device scan complete
[ 603.432000] scsi 5:0:0:0: Direct-Access Memorex TD Classic 003BPMAP PQ: 0 ANSI: 0 CCS
[ 603.660000] sd 5:0:0:0: [sdb] 4030464 512-byte hardware sectors (2064 MB)
[ 603.660000] sd 5:0:0:0: [sdb] Write Protect is off
[ 603.660000] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 603.660000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 603.664000] sd 5:0:0:0: [sdb] 4030464 512-byte hardware sectors (2064 MB)
[ 603.664000] sd 5:0:0:0: [sdb] Write Protect is off
[ 603.664000] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 603.664000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 603.664000] sdb: sdb1
[ 603.664000] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 603.664000] sd 5:0:0:0: Attached scsi generic sg1 type 0
[ 604.240000] UDF-fs: No partition found (1)
[ 604.284000] Unable to identify CD-ROM format.

Then I tried manual mount&#65306;sudo mount -t vfat /dev/sdb /mnt/usb
But failed again:
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

---

### Post by Xanadu on 2007-10-23
I also had the same problem on the X61. Seems that fstab was a bit incorrect - possibly due to the machine not having a CD drive, or possibly because I installed off of a USB stick. 

Either way the solution is simple. Edit /etc/fstab and comment out the line:
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by viveksri15 on 2007-10-26
Thankyou so much...

you solved my problem as well

I was not able to read a dual layer dvd (single layer was fine)

but now i am able to read dual layer as well


thanks again :)

---

### Post by Alistair_G on 2007-10-28
Many thanks for this as well - was trying to mount an external HD (Atlanta FG-700 media player) and kept getting error unable to mount volume.

My machine has no cd drive and once I had edited the file it now mounts perfectly.

---

### Post by jmomandia on 2007-11-03
IF that doesn't work, this may help. For my USB drive, the solution to Bug #151025 worked.
[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025) details as follows:

HERE'S THE FIX:
--------------------

Go into gconf-editor and navigate to /system/storage/default_options/vfat/mount_options, and then remove the "usefree" option from the list. Exit gconf-editor, and try hotplugging your drive again. It works :-)

So I did APPLICATIONS --> SYSTEM TOOLS --> CONFIGURATION EDITOR --> opened SYSTEM --> STORAGE --> DEFAULT OPTIONS --> right-clicked on MOUNT OPTIONS --> EDIT KEY --> removed USEFREE option from the list.

---

### Post by Qwertoi on 2007-11-06
> **jmomandia said:**
> IF that doesn't work, this may help. For my USB drive, the solution to Bug #151025 worked.
[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025) details as follows:

HERE'S THE FIX:
--------------------

Go into gconf-editor and navigate to /system/storage/default_options/vfat/mount_options, and then remove the "usefree" option from the list. Exit gconf-editor, and try hotplugging your drive again. It works :-)

So I did APPLICATIONS --> SYSTEM TOOLS --> CONFIGURATION EDITOR --> opened SYSTEM --> STORAGE --> DEFAULT OPTIONS --> right-clicked on MOUNT OPTIONS --> EDIT KEY --> removed USEFREE option from the list.

I tried this but was root and it didn't work (mount my USB stick) then. It works perfectly when I do it as the normal user. Suppose you have 50 users on the system, are there a smarter way to do this, or do all accounts have to do this?

---

### Post by hutxubix on 2007-11-16
Hi!!

I also have this problem, but I do not have System tools in the applications menu or a foder called /system...

And editing /etc/fstab do not solve my problem either.

I am on gutsy 64bits. Is it different?

---

### Post by Blufar on 2007-12-25
just open up terminal from Applications>Accessories. type in "gconf-editor" (w/o quotes) at the prompt then hit enter. Follow the rest of the instructions from there.

---

### Post by garyedwardjohnston on 2008-01-20
This did not work for me.

---

