---
title: "Mounting hardrive"
date: 2005-01-14
forum: General Help
---

### Post by Slowalker on 2005-01-14
Hi Everyone:

Hope this is where I should be asking this.

I'm a newbie at this Linux system. (Window's user only).

I do admit that I am impressed with the way Ubuntu loaded, picked up everything and set everything up ready to use! Congrats. Hopefully the next few months will prove to be just as satisfying.

My system is an AMD sempron 2400+, ASRock motherboard, 512mb RAM, 3G IDE hardrive and 500MB scsi hardrive.
I cannot see my hardrives.

 How do I "mount" these two drives so I can see and interact with them. That is, so that I can see them on the desktop or my disk or desktop file or the screen as my cd and floppy are mounted.
The 3G hardrive I assume is the Linux while the scsi should still be FAT32.

This is what I found out from searching:

They are not listed in the computer drop down menu.
The Disk file on the computer drop down menu shows Foloppy 1: floppy0, CD-ROM1: INCD, Filesystem, and network (no hardrives).

Grub file:
(hd0) /dev/hda  (this would be my 3 gig hardrive - boot)
(hd1) /dev/sda  (this would be my 500M scssi)

Device Manager:
shows the legacy floppy (1 volume), the scsi device Fujitsu (has one volume I assume still in fat 32 format), ide device (master) quantum fireball (has 3 volume), and LG cdrom (1 volume udf).

Terminal mode displays:

Filesystem Size Used Avail Use% Mounted on

/dev/hda2              18G  2.1G   15G  13% /
tmpfs                 507M     0  507M   0% /dev/shm
/dev/hdc1             190G  102G   89G  54% /mnt/hdc
/dev/hdd1             190G   70G  121G  37% /mnt/hdd
/dev/hde1             153G   25G  129G  17% /mnt/hde
/dev/hdf1              58G  1.4G   56G   3% /mnt/hdf


I assume that the tmpfs is my scsi drive. And I do understand 
that Linux partition the drive into three partition, but where do 
they get the 190G,150G and 58G partition from a 3G hardrive?

Thank you for your help
Dan

PS  Just did a reboot and checked booting sequence. It came up with the following:
  
      "Buffer IO errors on device hdb logical block from  256 to 277" 

      261 and 271 may have been OKJ

Thanks again
Dan

---

### Post by budyong on 2005-01-15
this may help

[www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by Slowalker on 2005-01-15
Thanks, apreciated

---

