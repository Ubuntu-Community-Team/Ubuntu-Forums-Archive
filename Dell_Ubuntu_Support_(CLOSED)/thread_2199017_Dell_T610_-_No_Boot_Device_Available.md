---
title: "Dell T610 - No Boot Device Available"
date: 2014-01-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by info23 on 2014-01-11
I'm trying to install Ubuntu 12-LTS on a Dell T610 server with a PERC H700, RAID1 & RAID5 configuration. I'm installing on the RAID-1; everything goes well until I reboot and the server simply does not find the boot record to proceed. I've used a live CD to make sure the partition /sda /sda1 is flagged as bootable & partition 1 is the active partition. I've also tried removing all signs of GPT to make sure grub is not getting confused. At this point I'm not sure of the direction I need to go. Anyone run into this and figure out how to resolve?

thanks,
Michael

---

### Post by oldfred on 2014-01-12
I do not know RAID, but boot flag/active partition is a Windows requirement, grub does not use it.

Not sure with hardware RAID where grub is installed. But I thought with RAID it is installed to the root of the RAID not the physical drive like sda.

---

### Post by info23 on 2014-01-12
Oldfred:

I should say first that our RAID1/RAID5 configuration is hardware RAID handled by the PERC H700 card. So it's being offered to the system as to "simple" hard drives, removing the RAID completely from any OS that loads.

Going on what I've read in the forums, I've tried "sudo fdisk /dev/sda" -> a -> 1 == which toggles partition to boot from? I did notice this was not set, so I tried it... no difference.
I've also tried "sudo parted -l" and "sudo fdisk /dev/sda" -> p = to see if the different partitions were even created, and they are. So, I'm back to the idea that grub just can't figure out where continue the boot process.
Tried "sudo gdisk -Z /dev/sda" to makre sure I didn't have any "dirty" artifacts left over from windows what-so-ever and as another thing to try... no difference.

I may not have the lingo correct as this is our first attempt to add a linux box to our environment, however, I hope this is more information to possibly assist with a resolution. 

Thanks.

---

### Post by oldfred on 2014-01-12
If BIOS sees it as one drive then installing to sda may be correct. Then the RAID installs to where it should be to work.

Post this. But if seen as /mapper as many RAID verisons are it may think it is LVM as that also is /mapper. You may have to specify.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by info23 on 2014-01-15
Oldfred, thanks for assisting me with this issue. I resolved it. It appears grub was saying the system was on /sdb for some reason and no matter what we did, it would not write the correct location. To remedy, I delete the second drive so only the RAID1 was available - forcing it to only use /sda /sda1, install the OS and it came right up. I then recreated the RAID5 and both drive are there and it seems to be fine.

regards,
Michael

---

### Post by tgalati4 on 2014-01-16
Make sure to update the BIOS and the PERC BIOS from Dell.  That can fix problems and improve performance.

---

