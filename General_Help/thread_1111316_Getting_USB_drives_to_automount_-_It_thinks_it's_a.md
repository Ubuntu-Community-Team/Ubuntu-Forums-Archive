---
title: "Getting USB drives to automount - It thinks it's a CD rom?"
date: 2009-03-30
forum: General Help
---

### Post by frammy7 on 2009-03-30
Ok, I know this one has been asked a lot - but I can't seem to find a simple answer to my problem...
I am running Xubuntu 8.04 (Hardy Heron), and when I plug my usb drive in to my PC I get the error:
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so.
```

It's a standard USB drive (2GB Kingston Datatraveller), and it works fine in XP, etc.
The output of my fdisk -l gives:
```
Disk /dev/sdb: 1999 MB, 1999568384 bytes
255 heads, 63 sectors/track, 243 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         244     1952672    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(242, 254, 63) logical=(243, 25, 37)
```

and my dmesg | tail gives:
```
[ 3336.140883] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[ 3336.143596] sd 15:0:0:0: [sdb] 3905407 512-byte hardware sectors (2000 MB)
[ 3336.144220] sd 15:0:0:0: [sdb] Write Protect is off
[ 3336.144229] sd 15:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 3336.144234] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[ 3336.144247]  sdb: sdb1
[ 3336.181233] sd 15:0:0:0: [sdb] Attached SCSI removable disk
[ 3336.181336] sd 15:0:0:0: Attached scsi generic sg1 type 0
[ 3342.895863] UDF-fs: No partition found (1)
[ 3342.970044] ISOFS: Unable to identify CD-ROM format.
```

So the USB drive seems to be recognised, but it has a problem with the physical/logical ending and is trying to mount it as a CD drive??? (there is NO cd drive in this PC by the way, as it doesnt have space for one!).

I can mount the USB drive manually in the terminal using the method shown on [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB), and that works 100% fine - it just won't automount + I was wondering if this one is a common problem + is there a simple fix for it??

(I've had a look in gconf-editor at /system/storage/defualt_options for vfat... and had a fiddle - but it didnt seem to work (so I put all the values back to what they were!))

So any help would be awesome, as I dont really want to have to mount them manually each time!!!

Many thanks!!!

---

### Post by frammy7 on 2009-03-30
Ok... hold the phone (well... hold off answering I guess...), I think I have found a solution - I just followed the help file on the kingston website... (sorry - I should have looked there before!)

The solution (for anyone else with the same problem) - have a look at [http://www.kingston.com/support/USBFLASHDRIVES/FAQ/faq_dti_hs_2.asp](http://www.kingston.com/support/USBFLASHDRIVES/FAQ/faq_dti_hs_2.asp)
Basically you have to edit the /etc/fstab file, and add the line it shows in the FAQ - then it will automount the kingston datatravellor for you...

I guess you have to add lines for sda1, sdb1, sdc1, etc for the number of drives you are using - which could be an issue - but hey, at least it works for now!

---

