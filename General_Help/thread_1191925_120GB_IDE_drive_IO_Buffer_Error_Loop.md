---
title: "120GB IDE drive I/O Buffer Error Loop"
date: 2009-06-19
forum: General Help
---

### Post by marc1uk on 2009-06-19
Hi guys, was hoping for some help with some HD teething troubles. Sorry, but (probably as usual) I'm a linux newbie, so if you need more info you'll have to be clear on what you need and how to get it. Thanks for the patience. 

I've just set up a Ubuntu 9.04 install on a 2GB IDE drive, alongside an XP install on a 20GB SATA drive. ntfs-3g support is working fine with read/write access on the 20GB windows drive. But I've also got another 120GB IDE drive, which is where the problem lies. 
I originally installed Ubuntu with just the SATA and Ubuntu drive installed. But introducing the second IDE drive, I now get a long string of errors following the Ubuntu loading bar:

[   20.087741] sd 1:0:1:0: [sdc] 240121728 512-byte hardware sectors (122942 MB)
[   20.087757] sd 1:0:1:0: [sdc] Write Protect is off
[   20.087759] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   20.087781] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.087844] sd 1:0:1:0: [sdc] 240121728 512-byte hardware sectors (122942 MB)
[   20.087856] sd 1:0:1:0: [sdc] Write Protect is off
[   20.087859] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   20.087879] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.087883]  sdc: sdc1
[   20.105502] sd 1:0:1:0: [sdc] Attached SCSI disk
[ 1430.026035] sd 1:0:1:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1430.026039] sd 1:0:1:0: [sdc] Sense Key : Medium Error [current] [descriptor]
[ 1430.026059] sd 1:0:1:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1430.026066] end_request: I/O error, dev sdc, sector 177471552
[ 1430.026070] Buffer I/O error on device sdc1, logical block 177471489
[ 1430.026076] Buffer I/O error on device sdc1, logical block 177471490
[ 1430.026079] Buffer I/O error on device sdc1, logical block 177471491
[ 1430.026082] Buffer I/O error on device sdc1, logical block 177471492
[ 1430.026085] Buffer I/O error on device sdc1, logical block 177471493
[ 1430.026088] Buffer I/O error on device sdc1, logical block 177471494
[ 1430.026091] Buffer I/O error on device sdc1, logical block 177471495
[ 1438.080851] sd 1:0:1:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1438.080855] sd 1:0:1:0: [sdc] Sense Key : Medium Error [current] [descriptor]
[ 1438.080875] sd 1:0:1:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1438.080882] end_request: I/O error, dev sdc, sector 177471552
[ 1438.080887] Buffer I/O error on device sdc1, logical block 177471489
[ 1438.080891] Buffer I/O error on device sdc1, logical block 177471490
[ 1438.080894] Buffer I/O error on device sdc1, logical block 177471491
[ 1438.080897] Buffer I/O error on device sdc1, logical block 177471492
[ 1438.081165] sd 1:0:1:0: [sdc] 240121728 512-byte hardware sectors (122942 MB)
[ 1438.092438] sd 1:0:1:0: [sdc] Write Protect is off
[ 1438.092446] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[ 1438.092530] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1438.092560] sd 1:0:1:0: [sdc] 240121728 512-byte hardware sectors (122942 MB)
[ 1438.092572] sd 1:0:1:0: [sdc] Write Protect is off
[ 1438.092575] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[ 1438.092595] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1446.199630] sd 1:0:1:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1446.199635] sd 1:0:1:0: [sdc] Sense Key : Medium Error [current] [descriptor]
[ 1446.199655] sd 1:0:1:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1446.199661] end_request: I/O error, dev sdc, sector 177733695
[ 1446.199669] Buffer I/O error on device sdc1, logical block 177733632
[ 1447.188074] sd 1:0:1:0: [sdc] 240121728 512-byte hardware sectors (122942 MB)
[ 1455.209323] sd 1:0:1:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1455.209327] sd 1:0:1:0: [sdc] Sense Key : Medium Error [current] [descriptor]
[ 1455.209347] sd 1:0:1:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1455.209353] end_request: I/O error, dev sdc, sector 177733695
[ 1455.209358] Buffer I/O error on device sdc1, logical block 177733632
[ 1455.209592] sd 1:0:1:0: [sdc] Write Protect is off
[ 1455.209595] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[ 1456.000304] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1456.009559] sd 1:0:1:0: [sdc] 240121728 512-byte hardware sectors (122942 MB)
[ 1456.009577] sd 1:0:1:0: [sdc] Write Protect is off
[ 1456.009580] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[ 1456.009601] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1465.082066] sd 1:0:1:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1465.082070] sd 1:0:1:0: [sdc] Sense Key : Medium Error [current] [descriptor]
[ 1465.082090] sd 1:0:1:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1465.082096] end_request: I/O error, dev sdc, sector 179306559
[ 1465.082101] Buffer I/O error on device sdc1, logical block 179306496
[ 1473.232770] sd 1:0:1:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1473.232774] sd 1:0:1:0: [sdc] Sense Key : Medium Error [current] [descriptor]
[ 1473.232794] sd 1:0:1:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1473.232800] end_request: I/O error, dev sdc, sector 179306560
[ 1473.232805] Buffer I/O error on device sdc1, logical block 179306497
[ 1473.232810] Buffer I/O error on device sdc1, logical block 179306498
[ 1473.232813] Buffer I/O error on device sdc1, logical block 179306499
[ 1473.232816] Buffer I/O error on device sdc1, logical block 179306500
[ 1473.232987] sd 1:0:1:0: [sdc] 240121728 512-byte hardware sectors (122942 MB)
[ 1481.255637] sd 1:0:1:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1481.255642] sd 1:0:1:0: [sdc] Sense Key : Medium Error [current] [descriptor]
[ 1481.255662] sd 1:0:1:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1481.255668] end_request: I/O error, dev sdc, sector 179306559
[ 1481.255675] Buffer I/O error on device sdc1, logical block 179306496
[ 1481.255681] Buffer I/O error on device sdc1, logical block 179306497
[ 1481.256368] sd 1:0:1:0: [sdc] Write Protect is off
[ 1481.256372] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[ 1481.256401] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1481.256428] sd 1:0:1:0: [sdc] 240121728 512-byte hardware sectors (122942 MB)
[ 1481.256461] sd 1:0:1:0: [sdc] Write Protect is off
[ 1481.256464] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[ 1481.256485] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

Eventually it all just grinds to a halt, and I just have to turn it off, unplug the drive, and all is well again. I get the same happening if I try to boot from the Ubuntu LiveCD. 

Any ideas on what might be causing this? I can't do much investigation, since if it's plugged in, i can't get anywhere, and if it's not, i can't very well investigate it. You guys are my only hope!

Thanks in advance

---

### Post by marc1uk on 2009-06-19
Probably unrelated, (although I'd appreciate help on it  too,) is that when the OS selection menu comes up, if I choose XP, I get a long blank stare from my PC, and after a while it just reboots. If I alter the boot order in the BIOS to boot from the 'Doze drive first, it works without a hitch, and indeed booting into windows, the 120GB drive works fine, confirming the drive's not lunched.

---

### Post by cariboo on 2009-06-19
I would almost suspect an unclean shutdown when the extrenal drive is disconnected. DO you umount the drives using the safely remove usb device applet in Windows before shutting down?

---

### Post by marc1uk on 2009-06-19
> **cariboo907 said:**
> I would almost suspect an unclean shutdown when the extrenal drive is disconnected. DO you umount the drives using the safely remove usb device applet in Windows before shutting down?
? Um, ... Admittedly I don't normally bother with the safely remove USB device applet in windows, but this is an IDE drive, not a USB one.

---

### Post by marc1uk on 2009-06-20
SO alright, I'm not really getting anywhere, but I thought I'd throw in some additional information in case it triggered any ideas.

Running sudo fdisk -l without the additional drive attached gives:
```
Disk /dev/sda: 4325 MB, 4325529600 bytes
255 heads, 63 sectors/track, 525 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         496     3984088+  83  Linux
/dev/sda2             497         525      232942+   5  Extended
/dev/sda5             497         525      232911   82  Linux swap / Solaris

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef18ef18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10010    80405293+   7  HPFS/NTFS

```Not sure if it's any help, but while I can't boot into the Ubuntu LiveCD with the additional drive attached, I can boot into a SLAX LiveCD. 
fdisk on this gives me: 
```
Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3438    27615703+   7  HPFS/NTFS
/dev/hda2   *        3439       19928   132455925    f  W95 Ext'd (LBA)
/dev/hda5            3439       19928   132455893+   7  HPFS/NTFS

Disk /dev/hdb: 4325 MB, 4325529600 bytes
255 heads, 63 sectors/track, 525 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         496     3984088+  83  Linux
/dev/hdb2             497         525      232942+   5  Extended
/dev/hdb5             497         525      232911   82  Linux swap

Disk /dev/hdc: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       10010    80405293+   7  HPFS/NTFS

```The corresponding /etc/fstab files are for SLAX: 
```

tmpfs            /                tmpfs       defaults         0   0
devpts           /dev/pts         devpts      gid=5,mode=620   0   0
proc             /proc            proc        defaults         0   0
/dev/fd0         /mnt/floppy      vfat,msdos  noauto,users,suid,dev,exec 0 0
/dev/hda1 /mnt/hda1 ntfs auto,users,suid,dev,exec 0 0
/dev/hda5 /mnt/hda5 ntfs auto,users,suid,dev,exec 0 0
/dev/hdb1 /mnt/hdb1 ext2 auto,users,suid,dev,exec 0 0
/dev/hdb5 swap swap swap 0 0
/dev/hdc1 /mnt/hdc1 ntfs auto,users,suid,dev,exec 0 0
/dev/hdd /mnt/hdd_cdrom iso9660 noauto,users,exec 0 0

```And for Ubuntu:
```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=fca91405-152c-48c8-ada1-711d07bb7663 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=9f8494e8-89f2-4fcf-b47c-d0a27e73d838 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb1 /media/windows ntfs-3g defaults,locale=en_GB.UTF-8 0 0

```Seems that I need to add:
```

/dev/sd*1 /media/windows2 ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sd*5 /media/windows3 ntfs-3g defaults,locale=en_GB.UTF-8 0 0

```sd* to my Ubuntu fstab, where * is the letter before a. 

Anyone care to fill in the details, or propose anything else?

---

### Post by marc1uk on 2009-06-20
Also wondering if it's a problem with GRUB. Though with the additional drive attached it seems to present me with the OS menu fine, I wondered perhaps if the device references change - i dunno, if sda was the IDE drive with linux before, it becomes sdb when i attach the new drive? Eh, i dunno. 
In other news, the device.map file contents are listed as
(hd0)    /dev/sda
(hd1)    /dev/sdb.

---

### Post by marc1uk on 2009-06-20
*tumbleweed drifts across a deserted forum* 
... hello..??
(bump)

---

### Post by marc1uk on 2009-06-23
Some updates because I'm STILL searching for a solution.
So far I have tried:
*Checking the md5 sum and the livecd disc from the menu - both come up fine, although I can't run the disc check when the new IDE drive is attached. When it's not attached, all systems OK. Odd that it should matter, since it's verifying the CD, not the HD, but there we go. 
*Tried burning to DVD rather than CD, and reducing the burn speed, also tried the alternate CD.
*adding all the suggested boot parameters i can find: irqpoll, ide=nodma, or ide=reverse, pci=nopci, noapic, nolapic, acpi=off, generic.all_generic_ide=1
*disabling the floppy drive in the BIOS settings
*modifying the fstab file to include the device, or the device.map, although the fact that it won't even boot from LiveCD suggests it's not a matter of adding the devices to these files
*changing the position or master/slave setting of the drive.
*the drive is connected with an 80-connector cable, not a 40-connector.
*power supply is a 500W, which should be more than sufficient to power my machine. 
*manually specifying the size of the drive, using hd0=<19929>,<2555>,<63> as <cyl>,<head>,<sect>, and varying hd0,hd1, hd2, since i'm not sure where it'll appear. 
*installed LILO instead of GRUB (since the SLAX LiveCD does work, and that uses LILO), but still to no avail. Presumably the problem is with the kernel casper scripts as opposed to the boot loader or configurations. 



I've got topics on this problem on 3 forums, which have recieved very little response and (obviously) no solutions/workarounds. Getting a bit frustrated - if I can't solve this, I've got no choice but to give up on the install, making my third (and probably last) attempt at installing a linux distribution. 

Please, any tips, suggestions, references... just put 'em in the quickreply box? Thanks

---

### Post by marc1uk on 2009-06-28
Well, eventually I backed up everything off the drive onto DVD (took a while on a 160GB drive!), tried to format it, although windows wasn't having it, and ground to a halt half-way through. Possibly it was the drive after all that. :| Eventually I split the drive into two, managed to format one partition in windows, and the other in linux. Couldn't format it using as ntfs using mkfs -t ntfs, getting a mfks.ntfs not found error, so ended up formatting it as a linux partition. And, after a few disk checks, it seems to have worked. Not an ideal solution, as 70GB of my HD is now accessible only to linux, but it's good enough. Solved, of a fashion.

---

