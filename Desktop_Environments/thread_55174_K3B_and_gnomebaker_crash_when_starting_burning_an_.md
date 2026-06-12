---
title: "K3B and gnomebaker crash when starting burning an audio cD"
date: 2005-08-07
forum: Desktop Environments
---

### Post by pirast on 2005-08-07
Hi,
a friend of mine has a strange problem: 

He tries to burn an audio cd (mp3 converted to wav). But it doesn't work:

K3B crashes when writing to the cd, Gnomebaker converts the first mp3 to wav, when burning it crashes too. 

In /var/log/messages I found the following thing:

> Aug  8 00:17:37 localhost kernel: attempt to access beyond end of device
Aug  8 00:17:37 localhost kernel: hdd: rw=0, want=68, limit=4
Aug  8 00:17:37 localhost kernel: attempt to access beyond end of device
Aug  8 00:17:37 localhost kernel: hdd: rw=0, want=1252, limit=4
Aug  8 00:17:37 localhost kernel: attempt to access beyond end of device
Aug  8 00:17:37 localhost kernel: hdd: rw=0, want=1028, limit=4
Aug  8 00:17:37 localhost kernel: UDF-fs: No partition found (1)
Aug  8 00:17:37 localhost kernel: attempt to access beyond end of device
Aug  8 00:17:37 localhost kernel: hdd: rw=0, want=68, limit=4
Aug  8 00:17:37 localhost kernel: isofs_fill_super: bread failed, dev=hdd, iso_blknum=16, block=16
Aug  8 00:28:24 localhost kernel: hdd: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Aug  8 00:28:24 localhost kernel: hdd: status error: error=0x00
Aug  8 00:28:24 localhost kernel: hdd: status timeout: status=0xd0 { Busy }
Aug  8 00:28:24 localhost kernel: hdd: status timeout: error=0xd0LastFailedSense 0x0d
Aug  8 00:28:24 localhost kernel: hdd: ATAPI reset complete
Aug  8 00:28:24 localhost kernel: hdd: status error: status=0x08 { DataRequest }
Aug  8 00:28:24 localhost kernel: hdd: status error: error=0x01IllegalLengthIndication
Aug  8 00:28:29 localhost kernel: hdd: status timeout: status=0xd0 { Busy }
Aug  8 00:28:29 localhost kernel: hdd: status timeout: error=0xd0LastFailedSense 0x0d
Aug  8 00:28:29 localhost kernel: hdd: ATAPI reset complete
Aug  8 00:28:29 localhost kernel: hdd: status error: status=0x08 { DataRequest }
Aug  8 00:28:29 localhost kernel: hdd: status error: error=0x01IllegalLengthIndication
Aug  8 00:28:35 localhost kernel: hdd: status timeout: status=0xd0 { Busy }
Aug  8 00:28:35 localhost kernel: hdd: status timeout: error=0xd0LastFailedSense 0x0d
Aug  8 00:28:40 localhost kernel: hdd: status timeout: status=0xd0 { Busy }
Aug  8 00:28:40 localhost kernel: hdd: status timeout: error=0xd0LastFailedSense 0x0d 

After this the system crashed and he rebooted.

His /etc/fstab looks like this:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/sda1        /mnt/winc        ntfs       ro,auto,user,uid=1000,gid=1000 0 0
/dev/sda5        /mnt/wind        ntfs       ro,auto,user,uid=1000,gid=1000 0 0

Please help,
Martin

---

