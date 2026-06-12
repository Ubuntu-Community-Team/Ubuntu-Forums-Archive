---
title: "Seeing a second hard drive"
date: 2005-11-27
forum: Desktop Environments
---

### Post by gergbee on 2005-11-27
Hi, 
I am pretty new to Linux but I am learning. My wife got a new computer so I grabbed the 10 GB slave drive out of her old one and stuck it in my Ubuntu test box.  

When I start up in Win 2000 the drive is recognized and if I use GParted in Ubuntu I can see the drive as well. I am guessing this means I have it hooked up correctly.

I have been trying to get the drive useable in Ubuntu with no success.  

I got some advice from another source so I will post what I did and the results.

**When I did fdisk /dev/hdb I got:**

[I]The number of cylinders for this disk is set to 1216.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)[/I]

**Then when I added  p I got:**

[I]Disk /dev/hdb: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   ?           1        1023     8217216    b  W95 FAT32
[/I]

**When I tried mount /dev/hdb1 /data -t vfat I got:**
[I]
mount: /dev/hdb1 is not a block device[/I]

I then searched around some more and found some advice in these forums.  

**I edited /etc/fstab **
[I]
/# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda4       /media/hda4     ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /media/hdb1     vfat    umask=000       0       0
[/I]

**But now when I do a sudo mount -a I get the following.**

[I][mntent]: line 1 in /etc/fstab is bad
mount: special device /dev/hdb1 does not exist[/I]

I am willing to reformat the drive but I need it to be seen in both the Win 2000 and the Ubuntu systems.

I have messed around so much that I get the feeling I am going to have to start from scratch here and I don't want to have to reinstall Ubuntu just to make it see a hard drive.

Hope someone can help.

Greg

---

### Post by cdhotfire on 2005-11-27
[quote=gergbee]Hi, 
I am pretty new to Linux but I am learning. My wife got a new computer so I grabbed the 10 GB slave drive out of her old one and stuck it in my Ubuntu test box. 

When I start up in Win 2000 the drive is recognized and if I use GParted in Ubuntu I can see the drive as well. I am guessing this means I have it hooked up correctly.

I have been trying to get the drive useable in Ubuntu with no success.  

I got some advice from another source so I will post what I did and the results.

**When I did fdisk /dev/hdb I got:**

[I]The number of cylinders for this disk is set to 1216.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)[/I]

**Then when I added  p I got:**

[I]Disk /dev/hdb: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   ?           1        1023     8217216    b  W95 FAT32
[/I]

**When I tried mount /dev/hdb1 /data -t vfat I got:**
[I]
mount: /dev/hdb1 is not a block device[/I]

I then searched around some more and found some advice in these forums.  

**I edited /etc/fstab **
[I]
/# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda4       /media/hda4     ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /media/hdb1     vfat    umask=000       0       0
[/I]

**But now when I do a sudo mount -a I get the following.**

[I][mntent]: line 1 in /etc/fstab is bad
mount: special device /dev/hdb1 does not exist[/I]

I am willing to reformat the drive but I need it to be seen in both the Win 2000 and the Ubuntu systems.

I have messed around so much that I get the feeling I am going to have to start from scratch here and I don't want to have to reinstall Ubuntu just to make it see a hard drive.

Hope someone can help.

Greg[/quote]

Do you have the "/" in from of the *"# /etc/fstab: static file system information." *?

If so, thats your problem.

---

### Post by tomwell on 2005-11-27
Just a thought i had a similar prob...

[http://www.ubuntuforums.org/showthread.php?t=89683](http://www.ubuntuforums.org/showthread.php?t=89683)

I am a noob too but when i reformated my fat32 partition in windows as a fat 32 then ubuntu recognised it... dont know why and know one commented on the reasons my fat32 got recognised after a format...(just make sure you select format filesystem type fat32...) I think you can just right click on the drive in windows....

Hope it works out for you let me know man!!

Peace

Tom

---

### Post by gergbee on 2005-11-27
[QUOTE=cdhotfire]Do you have the "/" in from of the *"# /etc/fstab: static file system information." *?

If so, thats your problem.[/QUOTE]

Yes, thanks for helping.  

Tried mounting again and I got 

[COLOR="DarkRed"]mount: special device /dev/hdb1 does not exist[/COLOR]

I will keep trying.

---

### Post by cdhotfire on 2005-11-27
[quote=gergbee]Yes, thanks for helping.  

Tried mounting again and I got 

[COLOR=DarkRed]mount: special device /dev/hdb1 does not exist[/COLOR]

I will keep trying.[/quote]

Check to make sure, that your partition is named hdb1 in gparted.

---

### Post by Brent Dax on 2005-11-27
That error makes it sound like the device file isn't available.  What do you get if you run the command "ls -l /dev/hd*"?

---

### Post by gergbee on 2005-11-27
[QUOTE=tomwell]Just a thought i had a similar prob...

[http://www.ubuntuforums.org/showthread.php?t=89683](http://www.ubuntuforums.org/showthread.php?t=89683)

I am a noob too but when i reformated my fat32 partition in windows as a fat 32 then ubuntu recognised it... dont know why and know one commented on the reasons my fat32 got recognised after a format...(just make sure you select format filesystem type fat32...) I think you can just right click on the drive in windows....

Hope it works out for you let me know man!!

Peace

Tom[/QUOTE]


Reformatting did the trick! Thanks a lot.

---

### Post by gergbee on 2005-11-27
[QUOTE=cdhotfire]Check to make sure, that your partition is named hdb1 in gparted.[/QUOTE]

It worked after I reformatted the drive (using Windows 2000) as fat32 as per another poster's advice.  Not sure why the old format didn't work but this did the trick.

Thanks for your input.

Greg

---

### Post by tomwell on 2005-11-27
Greg, I am so glad for you!!!

The other "posters" name is TOMWELL!! LOL

Yes me...

Lol 

Peace 

Tom

---

