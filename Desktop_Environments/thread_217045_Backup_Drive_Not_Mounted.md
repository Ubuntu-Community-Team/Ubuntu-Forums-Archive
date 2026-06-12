---
title: "Backup Drive Not Mounted"
date: 2006-07-16
forum: Desktop Environments
---

### Post by scubapro on 2006-07-16
Ubuntu Version: Dapper Drake/Updated

Hardware info for Backup Drive: [/ is mounted on hda1]

Properties: 

HD: ST380013A

80 gig

General Info:

Type: hard disk

Device: /dev/hdb

Speed: not available 

Partition Info:

Device: /dev/hdb1

Filesystem: ReiserFS

Access Path: none

Size: 74.53 GB [Free Space Not Available]

Status: Inaccessible


Problem: for some reason, Dapper Drake, does not recognize my backup hard drive, see above. 

When I go into Disk Manager, I can get it to mount the drive under /dev and it will work for that particular session, but as soon as I reboot, it goes back to 'disk not recognized/mounted' in Disk Manager. 

Anyone have any thoughts as to what I can do to get Ubuntu to permanently recognized the drive?:-| 

PS: I have not edited fstab, as I have not figured out how to do it yet.

Thanks,

Scubapro

---

### Post by aysiu on 2006-07-17
Try this... you'd substitute *reiserfs* for *ext3*, of course:
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

