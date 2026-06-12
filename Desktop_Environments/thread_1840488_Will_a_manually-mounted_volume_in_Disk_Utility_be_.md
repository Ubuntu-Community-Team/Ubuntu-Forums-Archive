---
title: "Will a manually-mounted volume in Disk Utility be remounted on a reboot?"
date: 2011-09-07
forum: Desktop Environments
---

### Post by jimerman on 2011-09-07
I did it - I replaced my server host OS from Windows to Ubuntu 11.04.  I'm thrilled.  The backup disk I left as formatted by Windows (SFS because it is a large volume).  So, I launched Disk Utility and mounted the partitions on the volume - it installed Samba, and I can access them from my Windows, Ubuntu and Mac clients, works great!!

But, I need to know if the volumes I mounted this way will be remounted after a reboot?  Or if not, then how do I mount it?  Do I have to edit one of the init files, add a mount command to mount the volumes?

Thanks for your answers!

---

### Post by haqking on 2011-09-07
> **jimerman said:**
> I did it - I replaced my server host OS from Windows to Ubuntu 11.04.  I'm thrilled.  The backup disk I left as formatted by Windows (SFS because it is a large volume).  So, I launched Disk Utility and mounted the partitions on the volume - it installed Samba, and I can access them from my Windows, Ubuntu and Mac clients, works great!!

But, I need to know if the volumes I mounted this way will be remounted after a reboot?  Or if not, then how do I mount it?  Do I have to edit one of the init files, add a mount command to mount the volumes?

Thanks for your answers!


I suspect you may need to edit your /etc/fstab

you can decide based on your configurations.

see here for an overview [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by jimerman on 2011-09-07
Thanks, very interesting.  I don't think it is showing all the info, though.  I have a 160GB hard drive with the OS on it, that must be /dev/sda, right?  Apparently the Ubuntu install partitioned it into 3 partitions.  /dev/sdb is supposed to have 2 partitions on it, which I see in Disk Utility, but don't show up in fdisk.  I should have a 43GB partition, and approximately 1.5TB partition.  Here's the fdisk output:

administrator@server1:~$ sudo fdisk -l
[sudo] password for administrator: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001a9c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19296   154987520   83  Linux
/dev/sda2           19296       19458     1300481    5  Extended
/dev/sda5           19296       19458     1300480   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x71586431

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001   42  SFS
administrator@server1:~$

---

### Post by jimerman on 2011-09-08
Thanks, haqking - that did work.  In Disk Utility it does show the device name of both volumes, so I was able to revise the fstab, and after reboot they mounted just great.  Next thing I am struggling with is Samba shares.  I edited my samba config file to specify a share for each mount, but the strange thing is the big one appears for a moment then disappears (e.g. I browse to \\server from a Windows client, and I see the share immediately after a `sudo restart smbd`, but if I double-click on it it gives me an error, and press F5 it disappears).  The other samba share works fine.  It couldn't have anything to do with the size of the volume, could it?

---

### Post by haqking on 2011-09-08
> **jimerman said:**
> Thanks, haqking - that did work.  In Disk Utility it does show the device name of both volumes, so I was able to revise the fstab, and after reboot they mounted just great.  Next thing I am struggling with is Samba shares.  I edited my samba config file to specify a share for each mount, but the strange thing is the big one appears for a moment then disappears (e.g. I browse to \\server from a Windows client, and I see the share immediately after a `sudo restart smbd`, but if I double-click on it it gives me an error, and press F5 it disappears).  The other samba share works fine.  It couldn't have anything to do with the size of the volume, could it?


what is the error message ? is the configuration the same as the other samba share ?

glad you got other bit solved too ;-)

---

### Post by jimerman on 2011-10-19
Thanks to Xerox for inventing the GUI!  I installed a Samba Server Configuration Tool GUI, this allowed me to manage the shares graphically.  I don't know what I must have missed, but it is all good now.  I also set up forwards to my printers, with IPP entries to support AirPrint so printing from the iPad to the non-AirPrint-compatible printers now works via Linux.

---

