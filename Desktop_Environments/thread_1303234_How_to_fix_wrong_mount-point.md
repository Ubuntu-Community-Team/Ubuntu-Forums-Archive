---
title: "How to fix wrong mount-point?"
date: 2009-10-28
forum: Desktop Environments
---

### Post by Azyx on 2009-10-28
Using Hardy 8.04 LTS cos later Ubuntu are not able to use KDETV with my TV-card :(

How-to fix automount?
When I insert an USB-memory i get this pop-up window.

"Cannot mount volume.
Invalid mount option when attempting to mount the volume."

When i run fdisk -l i get this:

************
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000866c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1271    10209276   83  Linux
/dev/sda2            1272       14844   109025122+  83  Linux
/dev/sda3           14845       15213     2963992+  82  Linux swap / Solaris
/dev/sda4           15214       19457    34089930   83  Linux

Disk /dev/sdb: 1030 MB, 1030225920 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c1427

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         125     1004031    6  FAT16
****************
And in fstab this:

****************
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=c24b3bd1-c6b3-4878-9708-25f1b5a65e85 /               ext3    relatime,erro$
# /dev/sda2
UUID=a218cdeb-5077-4917-bc0e-b4cea3432d8b /home           ext3    relatime     $
# /dev/sda3
UUID=335fdea7-73a9-4610-9637-354ba0829800 none            swap    sw           $
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
*************************

The problem seem to be that my USB-memory AND cdrom0 have the same driver sign (sdb). Fstab have /dev/sdb1 AS cdrom0 and fdisk -l my USB-memory. Where to changew so automount beguine to work? I have only one ide.cdrom i the machine,

PS. I are not able to use Bold, code or other formating here in the forum. Nothing happen when i click B for instance :(

---

### Post by Anonymousable on 2009-10-28
Hmm... Pastebin ([http://www.pastebin.com](http://www.pastebin.com) ) the output of ```
dmesg | tail
``` after plugging in the usb stick.

---

### Post by Azyx on 2009-10-28
> **Anonymousable said:**
> Hmm... Pastebin ([http://www.pastebin.com](http://www.pastebin.com) ) the output of ```
dmesg | tail
``` after plugging in the usb stick.

Azyx@intel:~$ dmesg | tail
[401900.284198] sd 6:0:0:0: [sdb] Write Protect is off
[401900.284201] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[401900.284203] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[401900.287845] sd 6:0:0:0: [sdb] 2012160 512-byte hardware sectors (1030 MB)
[401900.291329] sd 6:0:0:0: [sdb] Write Protect is off
[401900.291338] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[401900.291342] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[401900.291354]  sdb: sdb1
[401900.763230] UDF-fs: No VRS found
[401900.944833] ISOFS: Unable to identify CD-ROM format.
Azyx@intel:~$ 

Even here seems to be a conflict for sdb.

Could i only eraste some of the cdrom in fstab? I don want to do anyhing that **** up any more...

---

### Post by Azyx on 2009-10-28
I #-marked the:

/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

in /etc/fstab and it worked :)

---

