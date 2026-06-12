---
title: "I tried to mount my windowspartion  and got an error please help"
date: 2006-01-11
forum: General Help
---

### Post by angeleyes on 2006-01-11
I was using the guide to mount my windows patition and tried to save the changes to the mount and got this message:
[mntent]: line 1 in /etc/fstab is bad
[mntent]: line 6 in /etc/fstab is bad
can anyone tell mw how to fix this?Ive only had Ubuntu for a few days so this is all new to me
I appreciate any help you can give me
angeleyes

---

### Post by hillbilly on 2006-01-11
Post the contents of your /etc/fstab file. 

I assume you entered data into your fstab file and then did a > mount -a

Or if you did something else then let us know what it was !

---

### Post by towsonu2003 on 2006-01-11
could you paste the output of ```
cat /etc/fstab
``` This will show the [quote=hillbilly]contents of your /etc/fstab file[/quote]

---

### Post by angeleyes on 2006-01-11
yes hillbilly I did a mount -a
 and heres the fstab :
tc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2      /dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
/dev/hda3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I appreciate any help you can give me

---

### Post by defiantone on 2006-01-11
I had the same problem, but fortunately I saved my fstab from a prevoius install
First you need to make a dir in the /mnt dir called waht ever you want and then add these lines to your fstab.
Make sure that you have the correct device and flie system.

If you have NTFS (sorry about your luck) My advice is to reformat Winbloze FAT32 as ntfs is not secure and causes more problem then it's worth
I might have to install the ntfs kernel module for Ubuntu.


/dev/hda1	/mnt/Whatever	vfat	auto,defaults,user,umask=000 0 0 
/dev/hda2	/mnt/whatever	vfat	auto,defaults,user,umask=000 0 0

---

### Post by angeleyes on 2006-01-11
hmm hrad to reformat windows when I cant boot it....I lost a boot file (<Windows root>\system32\hal.dll.)for windows when i installed ubuntu..(I have no idea why or how)so I cant into my windows except through disks to look at my files in windows..so I cant refomat unless I can get a copy of that boot file to reinstall.Im not sure where in fstab to put that info..or which devices to put.
I feel really dumb now....but this is my first experience with a program like this -wanted to try something besides windows.

---

### Post by DoorGunner on 2006-01-11
This is my fstab..... Note i have a windows mount on hda2 and hda. I noticed your windows line is a little different from mine.....but i do know mine works....try and 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sdb        /media/usb0     auto    rw,user,noauto  0       0
/dev/hda2	/mnt/windows	ntfs	ro,defaults,umask=0222	0 0
/dev/hda3	/mnt/share	vfat    rw,defaults,umask=0000 0 0


make your windows line say this

/dev/hda2	/mnt/windows	ntfs	ro,defaults,umask=0222	0 0
it is a read only default .... for ntfs you dont want to be screwing up your ntfs  files by trying to over write with ext3 info from linux....(untill you get kernel 2.6.15 . This kernel has ntfs support but even then....do you want to take a chance?)

the error in your ext line is the same as mine.....you can not  see another linux partion. not to worry.

---

### Post by aysiu on 2006-01-11
[QUOTE=angeleyes]
**tc/fstab: static file system information.**
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
**/dev/hda2      /dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0**
/dev/hda3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0[/QUOTE] Lines 1 and 6 are bad for these reasons:
1 has no # sign in front of it. Put one in. 6 has two mount points--/dev/hda1 and /windows. I'd suggest you replace your entire /etc/fstab with this: ```
#/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2      /windows ntfs nls=utf8,umask=0222 0 0
/dev/hda3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
``` Then just to get a clean start, type these two commands ```
sudo umount /dev/hda2
sudo mount -a
```

---

### Post by angeleyes on 2006-01-11
thanks for all the help,..I think I got it fixed .

---

