---
title: "cant see windows drive using ubuntu live cd to access"
date: 2008-10-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by 4heid on 2008-10-29
I have a Dell system that is based on Vista using 2 250gb drives in a RAID0 configuration.
One of the disks, the one with the OS, indicates there is an error but that the RAID0 system is functional.
I tried booting through my Ubuntu Live CD as this is usually an easy way to see the drives and extract the files.
However, Ubuntu does not show the drives in COMPUTER.
I do see them in fdisk, one is listed with 3 partitions and having the OS in HPFS/NTFS format and the 2nd drive is listed as not having a partition table.

Why cant I see the drives? Is it because of the raid0? I just need to extract the data and this fix has worked for non raid setups where the Windows OS has crashed and wont boot.

---

### Post by 4heid on 2008-10-29
This is what I got when trying to do "sudo dmraid -ay"

ERROR: isw device for volume "ARRAY" broken on /dev/sdb in RAID set "isw_jibghiihe_ARRAY" 
ERROR: isw: wrong # of devices in RAID set "isw_jibghiihe_ARRAY" [1/2] on /dev/sdb 


Also says the NTFS volume on the first disk, sda1 is not valid.

When trying to do apt-get install ms-sys, it says ms-sys package not found as well, in order to try to reorganize the MBR to access.

The drives just dont show up, my usb thumb does but the 2 raid0 drives do not.

Any thoughts?

---

