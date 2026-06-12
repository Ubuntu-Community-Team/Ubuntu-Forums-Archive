---
title: "Re-install Ubuntu"
date: 2006-04-15
forum: Desktop Environments
---

### Post by gman2004 on 2006-04-15
All these started because I had to reinstall windows and I could not reinstall Grub. So I installed Ubuntu on an other drive (hde). I'm trying to recover data from an other drive (hdb)that I had install ubuntu before. These is the drives Ubuntu sees on my system.
> Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4998    40146403+   7  HPFS/NTFS

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          31      248976   83  Linux
/dev/hdb2              32       19929   159830685    5  Extended
/dev/hdb5              32       19929   159830653+  8e  Linux LVM

Disk /dev/hde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        9351    75111876   83  Linux
/dev/hde2            9352        9729     3036285    5  Extended
/dev/hde5            9352        9729     3036253+  82  Linux swap / Solaris

Disk /dev/hdf: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1   *           1       14592   117210208+   7  HPFS/NTFS

The ststem lets me mount the hdb1 partitions to /media but it will not let me mount the hb2.
I did System/ Administrator/ Disks/ Hard Disk/ Partitions/ Access Path /media/hdb2, but when I click enable nothing happens.
Also at Partition Properties I see the followings:
Device:   /dev/hdb5
Filesystem: Unformatted!!!!!!!!!
Access Path: /media/hdb2
Size: 142.53GB Free space not available!!!!!!!!!!
Status: Inaccassable

When I boot Ubuntu I get the error that hdb1 can not be mounted and check the dmesg to see the error log (Quote below)
> [4294675.677000] hde: WDC WD800BB-00CAA1, ATA DISK drive
[4294675.997000] hde: cache flushes not supported
[4294675.997000]  /dev/ide/host2/bus0/target0/lun0: p1 p2 < p5 >

I did sudo mount /dev/hdb5 /mnt and I get the error "mount: you must specify the filesystem type
"
I guess I need help!
Thank you one more time!

---

### Post by bscbrit on 2006-04-15
No, it will not let you mount /dev/hdb2 because it is not a usable partition, but rather a block of data that holds the information about the other partitions that live inside it.

/dev/hdb5 is also not a 'normal' partition but a linux volume manager which allows internal partitions to grow and resize as required.  I do not know how to mount one directly - only how to mount the partitions that it contained _providing_ you know what they were and their format.

You might have to wait until someone who knows much more than I do comes along to help. I'm fairly sure it can be done - I just don't know how!

---

### Post by bscbrit on 2006-04-15
See if the following help:

[http://www.die.net/doc/linux/HOWTO/LVM-HOWTO.html](http://www.die.net/doc/linux/HOWTO/LVM-HOWTO.html)

[http://www.digitalhermit.com/linux/lvm/](http://www.digitalhermit.com/linux/lvm/)

---

### Post by ubernoob on 2006-04-15
hdb2 is a logical partition an cannot be mounted. It contains the hdb5 partition. See my answer in [this thread]("http://www.ubuntuforums.org/showthread.php?t=157519").

---

### Post by gman2004 on 2006-04-15
Thx bscbrit, I have a lot of reading to do

---

### Post by gman2004 on 2006-04-15
ubernoob, I followed your link but I don't understan what do you mean.
I want to know if I can recover the data from that drive.
Thx again.

---

### Post by ubernoob on 2006-04-15
hdb2 (in your case) does not contain a system, but other partitions. it contains hdb5. So by recovering everything on hdb5 you have recovered everything on hdb2. Search for logical/extended partitions.

---

### Post by gman2004 on 2006-04-15
How do I search for logical/ extended partition? Have a link?
Thx for your time.

---

### Post by ubernoob on 2006-04-16
[QUOTE=gman2004]How do I search for logical/ extended partition? Have a link?
Thx for your time.[/QUOTE]
 You open a website called [Google]("http://www.google.com") and write "logical extended partition" (or something similar) in the searchbox and hit "Search". I'm sure you can manage that ;)

Sorry, but i don't have a link, so you have to google for it.

---

### Post by gman2004 on 2006-04-16
I'm sorry for wasting your time, but if I knew what I had to do to resolve, this I wouldn't ask! Even if I Google "logical extended partition", what am I looking for?
You might know what are you doing, but I'm not a computer expert. I'm trying to  learn and the only way to learn is to ask questions, I believe. You may tell me to look for it and be sure I'm trying, but I don't know what to look for even in GOOGLE! By the way, I though Google was a search engine, not a web site!

---

### Post by ubernoob on 2006-04-16
Try these:
[http://www.faqs.org/docs/linux_admin/x1139.html](http://www.faqs.org/docs/linux_admin/x1139.html)
[http://www.theeldergeek.com/hard_drives_01.htm](http://www.theeldergeek.com/hard_drives_01.htm)
[http://www.yale.edu/pclt/BOOT/PARTITIO.HTM](http://www.yale.edu/pclt/BOOT/PARTITIO.HTM)

google.com is a website. The technology on the site is a search engine ;)

---

### Post by gman2004 on 2006-04-16
Thank you,
I will keep you posted!

---

### Post by gman2004 on 2006-05-29
Here is my problem.
After a new windows re-installation, I could not get GRUB working. I did a new installation of UBUNTU. My drives are as follow:
> Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4998    40146403+   7  HPFS/NTFS

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          31      248976   83  Linux
/dev/hdb2              32       19929   159830685    5  Extended
/dev/hdb5              32       19929   159830653+  8e  Linux LVM

Disk /dev/hde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        9351    75111876   83  Linux
/dev/hde2            9352        9729     3036285    5  Extended
/dev/hde5            9352        9729     3036253+  82  Linux swap / Solaris

Disk /dev/hdf: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1   *           1       14592   117210208+   7  HPFS/NTFS

hda is my windows drive
hdb is my old Ubuntu installation
hde is my current Ubuntu instalaltion
hdf is a NTFS drive

I am trying to mount hdb so I can recover the data on it, but so far (after all research and reading) I had no luck of making it happen.

I hope someone can give me a pc of advice.

---

