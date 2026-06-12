---
title: "Grip not working"
date: 2006-09-16
forum: Desktop Environments
---

### Post by flebber on 2006-09-16
I was trying to get grip or Ripperx working.

HOwever neither can seem to see Cd's to rip them.

I wanted to use my cd drive for ripping. My drives are

system:/media/hdc    - DVD Drive
system:/media/hdd    - CD Drive

But filling this information into grip/ripper x wont work, I have tried inputting other versions to get it to work eg. /dev/hdd or /dev/cdrom or /dev/cdrom0 but alas no go. Any ideas

/etc/fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           xfs     defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda4       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0


---

### Post by flebber on 2006-09-17
Is anyone else having these problems ? Was there something simple to solve it ?

---

### Post by DoktorSeven on 2006-09-17
I'm not familiar with RipperX but with **grip**, putting /dev/hdd into Config->CD->CDRom device, then checking "Poll disk drive for new disk" works flawlessly here.  When inserting a music CD, grip should find the cd by itself and display the contents on the Tracks tab.

Is it completely ignoring inserting a disk?  Does any other cd player application see the CD to play it? (Note that music CDs cannot be *mounted* in Linux, so you won't see anything in /media/cdrom0 when a music CD is put in.)

---

### Post by flebber on 2006-09-18
Well it worked with /dev/hdd I swore I had that in before, but anyway thanks for the pointer all working.

---

