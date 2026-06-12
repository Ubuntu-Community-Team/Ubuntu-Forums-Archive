---
title: "Trying to Backup on Ubuntu and Drive &quot;Unable to Mount Location&quot;"
date: 2009-05-16
forum: General Help
---

### Post by Kuravid11 on 2009-05-16
Hi, I had my Windows XP crash on me, and the OS just won't load, so before I "repair" it or reinstall XP again, I wanted to backup my stuff via Ubuntu. I've never used Ubuntu before, but I came across this how-to ( [http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer) /) . When I go to Places>Computer I see the CD/RW Drive, "Mass Storage Device", and Filesystem, so I'm guessing "Mass Storage Device" is my hard drive. The problem is, when I try to open it, I get the popup "Unable to Mount Location - Can't mount file" without any "Details" link under it to click, so I don't know how to input a command to tell Ubuntu to let me into my hard drive so I can back up the files. Any help would be appreciated.

---

### Post by quixote on 2009-05-17
The way drives are named in "Places" is pretty braindead, unfortunately.  The easiest way to tell what's what is usually by size.  I assume you're booting from an Ubuntu LiveCD?  If so, the "Filesystem" is the operating system files currently in use, in other words the ones on the Live CD.  Other hard drives the system can see will usually be identified by size:  "10.8 GB"  or "500 GB" or whatever.  

If that's not enough for you to figure out which one is your Windows drive, then post a list of what the Places are that you see, and maybe we can try some more in-depth guessing. ;-)

If you're pretty sure it is your Windows drive, and it's giving you that message, that is not so good.  You may well still be able to get your data off, so don't panic, but it's a more complicated problem than running a LiveCD.  In the meantime, do NOT access that drive any more than you absolutely have to.  If it's lost its tiny mind, every time you access it, it can be overwriting files you may want.

---

### Post by Kuravid11 on 2009-05-17
I mentioned the Places listed - just  the CD/RW Drive, "Mass Storage Device", and Filesystem. When I look at the properties of "Mass Storage Device" the info's all just question marks. Also, I looked in Filesystem, and figured maybe my stuff could be in the "root" folder, but it gives me an error saying that I don't have permission to access it or something.
There's nothing on the hard drive that's so precious that I can't bear to lose it, but on the other hand I'd like to salvage a few things if that's possible.

---

### Post by Legace on 2009-05-17
Open Terminal, type in the following and post contents here:

```
sudo fdisk -l
```
AND
```
blkid
```

---

### Post by Kuravid11 on 2009-05-17
ubuntu@ubuntu:~$ sudo fdisk -l
blkid

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

---

### Post by quixote on 2009-05-17
Sounds like you need to rebuild the partition table.  This is one method, using testdisk: [http://ubuntuforums.org/showthread.php?p=7297013#post7297013](http://ubuntuforums.org/showthread.php?p=7297013#post7297013)

Alternatively try searching these forums for "recover partition" "partition recovery" and the like.

---

