---
title: "dvd drive not reading or burning"
date: 2006-07-03
forum: Desktop Environments
---

### Post by tich on 2006-07-03
before changing from Xp to ubuntu dapper i backed up my mp3 and avi files on dvd  (using a program called Drag&Drop) but after i installed dapper i couldn't read them. 
most of the time with these XP made dvd's i can't mount the drive but sometimes the dvd icon appears on my desktop and i can open it and browse the files. on extremely rare occasions i can even copy some of the files to the hard drive but if i was intending to copying 5 files somewhere between the 1st and the 3rd file it gets stuck (sometimes for 20 minutes or so) and says that the file cannot be copied.
i checked the dvd's on a XP machine the other day and they all worked fine on it.

then i tried to burn a data dvd using both the nautilus cd/dvd creator and graveman (others have been added to the list now too). in cd/dvd creator it wouldn't even begin the process; in graveman it went through all the motions of burning a dvd but the final result was a useless unreadable dvd (i would use them as coasters but it would be a tacky testement of failure).

i have installed all the restricted formats and DMA is turned on. the drive reads commercial dvd movies and data/music cd's. i don't have any data dvd's other than the ones i made on XP (which it doesn't read).

before installing Ubuntu my dvd drive worked fine so it shouldn't be a hardware problem. the drive is in a toshiba satellite 5200 notebook (dvd-rom sd-r6012).

--it has been about a month i'm starting to forget what music i listen too and i would love to read/burn dvd's again.

has anyone had a similar experence or is there any advice on how to fix this?

---

### Post by kzutter on 2006-07-03
I really don't know where to start, but I hate to see you out there hanging...

Here is the output of hdparm from my dvd burner
-----------------------------------
ken@u2:~$ hdparm /dev/hdd

/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
-------------------------
Compare it to yours - thet will get us started.

Also post your /etc/fstab file

-Ken
p.s. Its a holiday and I will be in and out, but will try to check in when I can

---

### Post by kzutter on 2006-07-04
Also check toshiba.com to see if there are any firmware updates to either the DVD or the BIOS

---

### Post by tich on 2006-07-05
so here is my hdparm output:
/dev/cdrom:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

/dev/cdrw:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

and here is the etc/fstab file:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0      0

hopefully this is helpful to those that can read it! :)

---

### Post by orb9220 on 2006-07-05
My only experience with these kind of problems is:

Permissions, Is the dvd drive mounting.

Did u run sudo gnome in a term and see if the drive is mounted and try to browse these disk.

If I select menu>Places>computer the drives is unmounted and I get a error unable to mount.

If I select >menu>Places>MyCD all the files are there.

I am still trying to make sense of permissions and access to my files.
I usally just create a shortcut on my panel and have it sudo nautilus everything because it frustrating to fiqure out when I have access to files.

Don't know if this helps because I don't know your skill level.

---

### Post by kzutter on 2006-07-05
orb92220 makes a good point, I assume you are a member of the admin group and the cdrom group.
If you are not sure, this command will list your group membership
```
groups
```

Lets see if we can get 32-bit IO going....

```
sudo hdparm -c1 /dev/hdb
```
then check to see if it stuck
```
sudo hdparm /dev/hdb
```
and if it did, cross your fingers and test it.

---

### Post by tich on 2006-07-06
well the 32-bit IO did stick.
and i crossed my fingers...

but when i tested it the first time it wouldn't mount and the second time it showed up (after a really long time reading the drive) but i could not copy the contents from the disk, nor would it open them from the disk (which i never tried before but i thought would be an interesting test-- i always just wanted the files on the hard drive)

---

### Post by tich on 2006-07-07
so i was checking out some stuff and this warning came up, i don't know if it has any actual effect on the dvd rom but i thought it would be better to include it:

** (nautilus:31297): WARNING **: No description found for mime type "x-special/device-block" (file is "cdrw"), please tell the gnome-vfs mailing list.

---

