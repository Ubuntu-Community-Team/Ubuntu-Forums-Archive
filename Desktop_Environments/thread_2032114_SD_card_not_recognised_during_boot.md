---
title: "SD card not recognised during boot"
date: 2012-07-23
forum: Desktop Environments
---

### Post by Patb on 2012-07-23
At boot time on my Acer Aspire One D255 netbook, it seems the driver module for the SD card reader is failing to operate early enough. Every time I boot, I get an error message "The disk drive for /media/homsd is not ready yet or not present". Then I am given an option to wait, skip, or choose manual recovery (a root shell). If I simply remove the SD card and then reinsert it, the SD card is recognised after couple of seconds, booting resumes normally and the card is mounted correctly at /media/homsd/ in accordance with the (last) line I have included in my fstab file. So I am presuming that whatever is preventing recognition of the SD card is solved by the time I reinsert the card. 

This has only happened since upgrading from 10.04 to 12.04. Previously, the card was recognised at boot time without any hassle. 

For what it is worth, here is a snippet from 'dmesg' for the situation where I remove and reinsert the card at boot time: 
```
[ 3.564223] scsi scan: INQUIRY result too short (5), using 36
[ 3.564241] scsi 4:0:0:0: Direct-Access PQ: 0 ANSI: 0
[ 3.566684] sd 4:0:0:0: Attached scsi generic sg1 type 0
[ 3.576471] sd 4:0:0:0: [sdb] Sector size 0 reported, assuming 512.
[ 3.576487] sd 4:0:0:0: [sdb] 1 512-byte logical blocks: (512 B/512 B)
[ 3.576496] sd 4:0:0:0: [sdb] 0-byte physical blocks
[ 3.580105] sd 4:0:0:0: [sdb] Write Protect is off
[ 3.580118] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 3.583853] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3.583864] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3.591463] sd 4:0:0:0: [sdb] Sector size 0 reported, assuming 512.
[ 3.600099] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3.600110] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3.623678] sd 4:0:0:0: [sdb] Unhandled sense code
[ 3.623688] sd 4:0:0:0: [sdb] Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[ 3.623699] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 3.623714] sd 4:0:0:0: [sdb] Add. Sense: Recorded entity not found
[ 3.623727] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 3.623753] end_request: critical target error, dev sdb, sector 0
[ 3.623764] Buffer I/O error on device sdb, logical block 0
 (Truncated - More of the same - keeps repeating about 6 lines)
[ 3.924072] sd 4:0:0:0: [sdb] Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[ 3.956111] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 3.956124] sd 4:0:0:0: [sdb] Add. Sense: Recorded entity not found
[ 3.956138] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 3.956165] end_request: critical target error, dev sdb, sector 0
[ 3.956202] sdb: unable to read partition table
[ 3.956213] sdb: partition table beyond EOD, enabling native capacity
[ 3.966770] sd 4:0:0:0: [sdb] Sector size 0 reported, assuming 512.
[ 3.977024] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 3.977034] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 12.970055] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 13.045542] Adding 2204668k swap on /dev/sda10. Priority:-1 extents:1 across:2204668k 
[ 13.048372] udevd[394]: starting version 175
[ 13.084823] keucr: module is from the staging directory, the quality is unknown, you have been warned.
[ 13.092111] usb --- usb_stor_init start
[ 13.092339] usbcore: registered new interface driver eucr
[ 13.092346] ENE USB Mass Storage support registered.
[ 13.223477] wmi: Mapper loaded
[ 13.350108] acer_wmi: Acer Laptop ACPI-WMI Extras
[ 13.350152] acer_wmi: Function bitmap for Communication Button: 0x1
[ 13.350403] acer_wmi: Brightness must be controlled by generic video driver
[ 13.352613] input: Acer WMI hotkeys as /devices/virtual/input/input6
[ 13.625111] cfg80211: Calling CRDA to update world regulatory domain
[ 13.731057] audit_printk_skb: 4 callbacks suppressed
[ 13.731068] type=1400 audit(1342946739.816:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=474 comm="apparmor_parser"
[ 13.732658] type=1400 audit(1342946739.820:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=474 comm="apparmor_parser"
[ 13.733489] type=1400 audit(1342946739.820:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=474 comm="apparmor_parser"
[ 13.873857] Linux video capture interface: v2.00
[ 14.577450] Dev sdb: unable to read RDB block 1
[ 14.577712] sdb: unable to read partition table
[ 14.577726] sdb: partition table beyond EOD, truncated
[ 14.578148] sd 4:0:0:0: [sdb] 31116288 512-byte logical blocks: (15.9 GB/14.8 GiB)
[ 14.578301] sd 4:0:0:0: [sdb] No Caching mode page present
[ 14.578312] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 14.578323] sd 4:0:0:0: [sdb] Attached SCSI disk
```

The kernel module I use to recognise the card reader is "keucr" which I have installed and which works fine. To ensure the keucr module is started at boot time I have included "keucr" in the file /etc/modules. 

The file system on the SD card in question appears to be okay:
```
pat@pat-AOD255:~$ sudo fsck -V -r /dev/sdb1 
fsck from util-linux 2.20.1
[/sbin/fsck.ext2 (1) -- /media/homsd] fsck.ext2 -r /dev/sdb1 
e2fsck 1.42 (29-Nov-2011)
homsd: clean, 58551/972944 files, 2083215/3887722 blocks
```

Can anyone give me a hint as to why the card is not recognised at boot time? Thanks in advance. 

Cheers, Pat.

---

