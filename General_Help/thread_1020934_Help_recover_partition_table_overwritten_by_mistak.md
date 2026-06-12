---
title: "Help recover partition table overwritten by mistake"
date: 2008-12-24
forum: General Help
---

### Post by grepsky on 2008-12-24
I made a stupid mistake of overwriting the beginning of my ubuntu hardy laptop hard disk using the command [FONT="Fixedsys"][SIZE="1"]sudo dd if=diskboot.img of=/dev/sda[/SIZE][/FONT]. My actual intention was to create a USB disk using a linux boot image diskboot.img which is 12MB in size.  

I haven't rebooted yet and the laptop is running fine. But I know the partition table is screwed and some data in the beginning of the disk is lost.

fdisk complains. The partition table is missing fs types and extended partition where I have installed ubuntu.
[FONT="Fixedsys"][SIZE="1"]$ sudo fdisk -l
[sudo] password for vimal: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde8e7bb0

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?      188019      188051      253319   e4  SpeedStor
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?       62656      186401   993984023   98  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?      105611      225119   959953209   7d  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda4   ?         331         849     4161536    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
[/SIZE][/FONT]

Here are the details about the mounted partitions.
[FONT="Fixedsys"][SIZE="1"]$ mount | grep sda
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
/dev/sda2 on /media/c type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)[/SIZE]
[/FONT]

I tried gpart.  But it doesn't detect it right as the extended partition is missing and the partition-1 has wrong start and end numbers.
[SIZE="1"]$ sudo gpart /dev/sda

Begin scan...
Possible partition(Windows NT/W2K FS), size(3mb), offset(11367mb)
Possible partition(Linux ext2), size(52772mb), offset(59402mb)
Possible partition(Linux swap), size(2296mb), offset(112174mb)
End scan.

Checking partitions...
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
Partition(Linux ext2 filesystem): primary 
Partition(Linux swap or Solaris/x86): primary 
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 3mb #s(6173) s(23281272-23287444)
   chs:  (1023/254/63)-(1023/254/63)d (1449/49/1)-(1449/146/62)r

Primary partition(2)
   type: 131(0x83)(Linux ext2 filesystem)
   size: 52772mb #s(108077696) s(121655583-229733278)
   chs:  (1023/254/63)-(1023/254/63)d (7572/181/1)-(14300/59/62)r

Primary partition(3)
   type: 130(0x82)(Linux swap or Solaris/x86)
   size: 2296mb #s(4702256) s(229733343-234435598)
   chs:  (1023/254/63)-(1023/254/63)d (14300/61/1)-(14592/239/62)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

[/SIZE]

Does linux cache the partition table?  If so is it possible to write to disk the PT that ubuntu has in memory now? (it is perfectly working fine for the past 12h and I am afraid will stop working on reboot).  I dont care about recovering /dev/sda2 which has an unused windows installation.

any help is much appreciated. Thanks.

---

### Post by dcstar on 2008-12-24
> **grepsky said:**
> I made a stupid mistake of overwriting the beginning of my ubuntu hardy laptop hard disk using the command [FONT="Fixedsys"][SIZE="1"]sudo dd if=diskboot.img of=/dev/sda[/SIZE][/FONT]. My actual intention was to create a USB disk using a linux boot image diskboot.img which is 12MB in size.  

I haven't rebooted yet and the laptop is running fine. But I know the partition table is screwed and some data in the beginning of the disk is lost.
.......
any help is much appreciated. Thanks.

There are rescue CDs that you can download with partition table editing tools on them - but they are tricky to use. I think that I have used one previously called "Ranish" that had such a tool on it, you may want to do a web search and try it out.

---

### Post by caljohnsmith on 2008-12-24
As long as you haven't rebooted yet, I would recommend backing up any important data in the Ubuntu partition you are in onto another drive. What was on sda1? That's the partition you won't easily be able to recover since you overwrote its beginning. I can help you try to recover your other partitions though with "testdisk" if you want, but how about saving all your important data first and then we can work from there.

---

### Post by grepsky on 2008-12-24
Thank you John. I have backed up all the important data. sda1/2 are not important to me. All I want is to make sure sda5 (extended partition on which ubuntu '/' is mounted to) is intact and the MBR is set so that I can boot into ubuntu.

I am few hours away from the affected laptop which I left at work. I will try out testdisk and get back with the result tomorrow morning your time.  It would be great if you could share any pointers that would help me in the process.

---

### Post by caljohnsmith on 2008-12-24
OK, to use testdisk, you would first want to make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
**If you are using Version 6.8:**
After starting testdisk with the above command, choose "no log", select HDD and "Proceed", "Intel", "Analyze", "Proceed", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Search!" so it does a deeper search, which could take a while. Once it is done and shows you a list of partitions, use the up/down arrow keys to select each partition, and for the partitions that look like they might be what you want to recover, press "p" to get a directory listing. If you successfully get a directory listing, then it should be safe to recover that particular partition, so mark it as either "P" or "L" for primary or logical partition. Since the partitions you want to recover are logical partitions it sounds like, you would mark them as "L" if you can. All the other partitions that you don't want to recover (or are invalid), mark with "D" to delete. Once you are sure you have everything marked appropriately, proceed to the next screen where you can write the new partition table. Then reboot your Live CD again, and you will probably need to follow the directions at the end of this post in order to reinstall Grub, because your partition numbers might change. Feel free to post the results of the "deep scan" if you would like more specific help though about recovering your partitions.

**If you are using Version 6.9:**
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Once it is done and shows you a list of partitions, use the up/down arrow keys to select each partition, and for the partitions that look like they might be what you want to recover, press "p" to get a directory listing. If you successfully get a directory listing, then it should be safe to recover that particular partition, so mark it as either "P" or "L" for primary or logical partition. Since the partitions you want to recover are logical partitions it sounds like, you would mark them as "L" if you can. All the other partitions that you don't want to recover (or are invalid), mark with "D" to delete. Once you are sure you have everything marked appropriately, proceed to the next screen where you can write the new partition table. Then reboot your Live CD again, and you will probably need to follow the directions at the end of this post in order to reinstall Grub, because your partition numbers might change. Feel free to post the results of the "deep scan" if you would like more specific help though about recovering your partitions.

[B]
To restore Grub (if you need to):[/B]
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know how it goes or if you run into problems. :)

---

