---
title: "Btrfs on 2nd partition of USB HDD automounts RO"
date: 2012-08-15
forum: Desktop Environments
---

### Post by dg1727 on 2012-08-15
Hi there, 

I have a user with an Xubuntu 12.04.1 laptop, 32-bit.   He needs to use a USB hard disk drive which has 2 partitions:  the 1st  partition is NTFS and the 2nd partition is Btrfs.  

When he plugs  in the hard drive, both partitions auto-mount OK, except that the Btrfs  partition automounts read-only.  How can the OS be set up so that the  Btrfs will automount read/write?  

The "dmesg" command shows the following on plug-in of the drive:  

```

[ 7253.520087] usb 2-4: new high-speed USB device number 11 using ehci_hcd
[ 7253.656344] scsi11 : usb-storage 2-4:1.0
[ 7256.651677] scsi 11:0:0:0: Direct-Access     TOSHIBA  External USB 3.0 0001 PQ: 0 ANSI: 6
[ 7256.654722] sd 11:0:0:0: Attached scsi generic sg2 type 0
[ 7256.656970] sd 11:0:0:0: [sdb] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[ 7256.660515] sd 11:0:0:0: [sdb] Write Protect is off
[ 7256.660534] sd 11:0:0:0: [sdb] Mode Sense: 1f 00 00 08
[ 7256.662509] sd 11:0:0:0: [sdb] No Caching mode page present
[ 7256.662523] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[ 7256.668478] sd 11:0:0:0: [sdb] No Caching mode page present
[ 7256.668498] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[ 7256.673838]  sdb: sdb1 sdb2
[ 7256.681474] sd 11:0:0:0: [sdb] No Caching mode page present
[ 7256.681493] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[ 7256.681507] sd 11:0:0:0: [sdb] Attached SCSI disk
[ 7257.545702] device label external devid 1 transid 19 /dev/sdb2
[ 7257.546790] btrfs: disk space caching is enabled 

```

Neither  the "usbmount" nor "pmount" packages are installed, but "thunar-volman"  is installed.  I did install "pmount" only to find that it appears to  be meant to be invoked manually, so I un-installed it again.  

"uname -rv" reports:
```
3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:04:05 UTC 2012
```

The "groups" command shows that the user is a member of the following (in addition to a group named after his username):  
```
adm dialout fax cdrom floppy tape sudo dip video plugdev fuse lpadmin sambashare
```

The "mount" command shows for the Btrfs partition in question:  
```
/dev/sdb2 on /media/[partition_label] type btrfs (rw,nosuid,nodev,uhelper=udisks)
```

(I have substituted [partition_label] for the partition label, which is all letters, no punctuation marks.)  

Because  "mount" shows "rw", does that mean that it is the configuration of  Btrfs, not the configuration of automounting, that is at issue?  

I appreciate any help.

---

### Post by dg1727 on 2012-08-17
If you have any suggestions about this issue, please reply to this thread.   Thanks.

---

