---
title: "ZFS will not online device"
date: 2011-07-18
forum: Desktop Environments
---

### Post by gratou on 2011-07-18
Can anyone see why this is happening?
I am starting to go mad having tried even swapping sata controllers.

[SIZE="1"][FONT="Courier New"]chris@bob:~$ sudo zpool status
  pool: tank1
 state: DEGRADED
status: One or more devices could not be opened.  Sufficient replicas exist for
	the pool to continue functioning in a degraded state.
action: Attach the missing device and online it using 'zpool online'.
   see: [http://www.sun.com/msg/ZFS-8000-2Q](http://www.sun.com/msg/ZFS-8000-2Q)
 scrub: none requested
config:

	NAME                                                            STATE     READ WRITE CKSUM
	tank1                                                           DEGRADED     0     0     0
	  raidz1-0                                                      DEGRADED     0     0     0
	    disk/by-id/scsi-SATA_ST2000DL003-9VT_5YD3EBD6-part1         ONLINE       0     0     0
	    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2H7J1EB208362-part1    ONLINE       0     0     0
	    disk/by-id/scsi-SATA_WDC_WD20EADS-00_WD-WCAVY0204746-part1  ONLINE       0     0     0
	    disk/by-id/scsi-SATA_WDC_WD20EADS-00_WD-WCAVY0910084-part1  ONLINE       0     0     0
	    disk/by-id/scsi-SATA_WDC_WD20EARS-00_WD-WCAVY2660000-part1  UNAVAIL      0     0     0  cannot open

errors: No known data errors

chris@bob:~$ sudo zpool online tank1 /dev/disk/by-id/scsi-SATA_WDC_WD20EARS-00_WD-WCAVY2660000-part1
cannot online /dev/disk/by-id/scsi-SATA_WDC_WD20EARS-00_WD-WCAVY2660000-part1: no such device in pool

chris@bob:~$ sudo zpool online tank1 disk/by-id/scsi-SATA_WDC_WD20EARS-00_WD-WCAVY2660000-part1
cannot online disk/by-id/scsi-SATA_WDC_WD20EARS-00_WD-WCAVY2660000-part1: no such device in pool

chris@bob:~$ ls /dev/disk/by-id/s* | grep 0000
/dev/disk/by-id/scsi-SATA_WDC_WD20EARS-00_WD-WCAVY2660000
/dev/disk/by-id/scsi-SATA_WDC_WD20EARS-00_WD-WCAVY2660000-part1
[/FONT][/SIZE]
I use /dev/by-id names because the /dev/sdx names change all the time upon reboot :(

Thank you.

---

