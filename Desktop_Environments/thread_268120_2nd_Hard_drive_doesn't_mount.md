---
title: "2nd Hard drive doesn't mount"
date: 2006-09-29
forum: Desktop Environments
---

### Post by theeru on 2006-09-29
Hello.

I recently installed Ubuntu 6.06 on my HP 2.6 GHz P4. I was running Windows but I decided to cleanse myself. I had 250 GB external hard drive with a VFAT file system that the power supply stopped working on, so I stripped it down and made it internal and it was working fine under XP. However, Ubuntu won't mount the drive. When I click drive in File Browser, I get an error message saying:

Unable to mount the selected volume
error: device /dev/hdb1 is not removable

error: could not execute pmount


The drive is a Maxtor 6L250R0. I have over 100 GB of data on the drive that I want to save. Basically, everything that I backed up from when I was running XP. I'd appreciate any help. Thanks in advance.

---

### Post by aysiu on 2006-09-29
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by mattyj on 2006-09-29
I have a very similar situation, and posted this earlier.  Eager to hear replies.

Thank You.

---

### Post by mattyj on 2006-09-29
Hello,

If I simply want to add a second drive with ext3 formatting what would the correlary be for that:

This is what you did for windows.  I have been playing, but still no luck.  Thank you.

From your site:

This is what it might look like before we change it:
proc /proc proc defaults 0 0
/dev/hda6 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 /home ext3 defaults 0 2
/dev/hda1 /media/hda1 ntfs defaults 0 0
/dev/hda7 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0

This is what it should look like after we change it:
proc /proc proc defaults 0 0
/dev/hda6 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 /home ext3 defaults 0 2
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
/dev/hda7 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0

---

### Post by mattyj on 2006-09-29
For example I have two drives sda and sdb.  I am booting from sda.  This is how I setup my /etc/fstab, but it still doesn't work:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/sdb	/dev		ext3	defaults,errors=remount-ro 0       1
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

When I try to mount I get this:

mj@mj-desktop:~$ sudo mount -a
mount: /dev/sdb already mounted or /dev busy
mount: according to mtab, udev is already mounted on /dev
mj@mj-desktop:~$

Thank You for your help.

---

### Post by danderson3 on 2006-09-29
did you compile your own kernel or are you running a kernel
from the repos?

---

### Post by danderson3 on 2006-09-29
also I note the ref to pmount - are you trying to mount as a user
or as root?

David

---

### Post by theeru on 2006-09-29
I didn't compile the system. It is all binaries from the repositories. But I ended up following the instructions at [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) for editing fstab to setup a VFAT partition then remounted and everything works fine now.

Thank you all very much.

---

### Post by mistab1034 on 2006-09-29
> **mattyj said:**
> 
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/sdb	/dev		ext3	defaults,errors=remount-ro 0       1


Not sure if this is your problem, but notice how on the first 2 lines there are numbers after the sda, ie sda1 and sda5, well you don't have one for the sdb line. The number represents the partition number on the drive. Assuming you've formatted the drive, and it only has one partition you should be able to mount it on /dev/sdb1. Just a thought.

---

