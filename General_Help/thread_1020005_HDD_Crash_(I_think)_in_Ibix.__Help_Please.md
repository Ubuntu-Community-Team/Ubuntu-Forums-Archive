---
title: "HDD Crash (I think) in Ibix.  Help Please"
date: 2008-12-23
forum: General Help
---

### Post by Runey on 2008-12-23
I've been using Ubuntu on my Laptop for around a year now an upgraded to Ibix when it came out.

The other day after shutting down my laptop, when I went to turn it on again I got a GRUB error - Error 18 - and the computer just hung there.

My knowleged of linux is limited (I know I've had it for a year but never really tinkered much) so googled for some answers.  Mostly what I found was that it could be a problem with the MBR - and it mostly occurs on a new install or re-install which is not the case with me.

I followed a few answers offered as solutions and it still didn't help.

More concerning, I booted into Linux using a Live boot CD (Heron).  If it was a problem with the MBR then I should at least be able to see all my files.

I can't.

I can see the drive and click on it.  It then takes around 5 minutes (literally) but eventually comes up with the folders in the root.  I click on the home drive (as i want to save my photos) and it comes up with that little spinning wheel and does nothing.  I've left it overnight even and even though the wheel is replaced with the arrow, there are no files displayed.

So... two questions in order of importance.

1. What can i do to save my files? The HDD is in a linux format (not FAT or NTFS).  I have a windows desktop but no easy way to connect my laptop HDD to this PC so would prefer a solution that allows me to get the files off my leptop onto a USB drive.

2. If i can boot into my Laptop with a live CD, does this just mean that my HDD is dead (and not my entire laptop) in which case if i got a new HDD my laptop will live to fight another day?

Any help would be massivley appreciated!

Thanks

---

### Post by oilchangeguy on 2008-12-23
> **Runey said:**
> I've been using Ubuntu on my Laptop for around a year now an upgraded to Ibix when it came out.

The other day after shutting down my laptop, when I went to turn it on again I got a GRUB error - Error 18 - and the computer just hung there.

My knowleged of linux is limited (I know I've had it for a year but never really tinkered much) so googled for some answers.  Mostly what I found was that it could be a problem with the MBR - and it mostly occurs on a new install or re-install which is not the case with me.

I followed a few answers offered as solutions and it still didn't help.

More concerning, I booted into Linux using a Live boot CD (Heron).  If it was a problem with the MBR then I should at least be able to see all my files.

I can't.

I can see the drive and click on it.  It then takes around 5 minutes (literally) but eventually comes up with the folders in the root.  I click on the home drive (as i want to save my photos) and it comes up with that little spinning wheel and does nothing.  I've left it overnight even and even though the wheel is replaced with the arrow, there are no files displayed.

So... two questions in order of importance.

1. What can i do to save my files? The HDD is in a linux format (not FAT or NTFS).  I have a windows desktop but no easy way to connect my laptop HDD to this PC so would prefer a solution that allows me to get the files off my leptop onto a USB drive.

2. If i can boot into my Laptop with a live CD, does this just mean that my HDD is dead (and not my entire laptop) in which case if i got a new HDD my laptop will live to fight another day?

Any help would be massivley appreciated!

Thanks

hard drive is probably not dead. grub error 18 has to do with the way ubuntu sees the hard drive, and the bios sees the hard drive. for example, you have an older computer, and install a 200gb hard drive.. and the bios shows under auto it is max 85000mb. this will cause a problem with grub being installed within the first 1036mb on the hard drive. not sure if this is your issue. have you made any changes to the computer?

---

### Post by oilchangeguy on 2008-12-23
also you should be able to run the computer from the live cd, and get your data. and there are ide adapters (i got one on ebay) available the allow you to connect a laptop hard drive to a desktop computer.

---

### Post by Runey on 2008-12-23
Thanks Mate.

I haven't made any changes to the computer so, i think that it's strange that it's an Error 18...

Tried the live CD route but linux still can't read the HDD.  Am looking at getting an external case today to connect the USB drive to the Windows Desktop - though are there windows tools that can read a (potentially) crashed linux drive?

Or are there some tools on the ubuntu live cd I can use to force it to access my files?

Any other thoughts welcome...

---

### Post by oilchangeguy on 2008-12-23
> **Runey said:**
> Thanks Mate.

I haven't made any changes to the computer so, i think that it's strange that it's an Error 18...

Tried the live CD route but linux still can't read the HDD.  Am looking at getting an external case today to connect the USB drive to the Windows Desktop - though are there windows tools that can read a (potentially) crashed linux drive?

Or are there some tools on the ubuntu live cd I can use to force it to access my files?

Any other thoughts welcome...

i don't think it's a good sign that the live cd won't read the drive. i've had some drives become unbootable, and just slaved them to another computer, and get the data from them.

---

### Post by albinootje on 2008-12-23
> **Runey said:**
> 
Tried the live CD route but linux still can't read the HDD.

Can you post the output of the following in a terminal during the "live" session :
```

sudo fdisk -l

```
And also during the "live" session :
```

sudo apt-get install testdisk

```
and use that.
For documentation, see here :
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Runey on 2008-12-23
Yup.  I'll post that output a soon as I get home tonight and will let you know.

Thanks for your help.

---

### Post by Runey on 2008-12-24
ok.  The output of the fdisk command was

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfbaefbae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris


I'll get on to the testdisk now...

Does the above help at all?

---

### Post by albinootje on 2008-12-24
> **Runey said:**
> ok.  The output of the fdisk command was

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfbaefbae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris


I'll get on to the testdisk now...

Does the above help at all?

This looks good. 
Partitions are visible, and no error messages,

---

### Post by plucky on 2008-12-24
You need to mount the HDD to access the information when using the Live CD

Try from a terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
df -h
sudo blkid
```

and see what that produces.

Good Luck

---

