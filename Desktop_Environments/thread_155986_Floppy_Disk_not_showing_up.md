---
title: "Floppy Disk not showing up?"
date: 2006-04-06
forum: Desktop Environments
---

### Post by Gracye on 2006-04-06
My floppy drive isn't showing up and I have no idea what to type in to check where it is to mount it. Help!

---

### Post by waster on 2006-04-06
In KDE, can't you configure desktop, go to device tab, then select unmounted/mounted floppy. If it's not in /etc/fstab, though, it won't come up.

---

### Post by Gracye on 2006-04-06
it's under lists of devices, and when I tried /etc/fstab it said permission was denied?

---

### Post by stig on 2006-04-06
Have a look at the last reply in this thread - it might help!

[http://www.ubuntuforums.org/showthread.php?t=147980&highlight=floppy+disk](http://www.ubuntuforums.org/showthread.php?t=147980&highlight=floppy+disk)

---

### Post by Gracye on 2006-04-06
ok I tired it and I got this error when trying to mount it:

mount: /dev/fd0 is not a valid block device

here is my fstab: (if that helps at all)
[qupte]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /media/hda3     ntfs    defaults        0       0
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0
[/quote]

---

### Post by Gracye on 2006-04-06
ahh it's working now. I just stuck in a floppy and looked under places.  It wasn't doing that before, but I still get the error when trying to mount it o.O

---

### Post by Sef on 2006-04-06
There's a bug in Breezy that is fixed in Dapper, so I am looking foward to that fix.

---

### Post by Chuck_W on 2006-04-06
I'm very new to Ubuntu and was also puzzled when I couldn't get to either the floppy or the internal Zip drives on my P3 800. Downloading and installing the updates/bug fixes took care of the problem. On boot up there is an icon on the upper right part of the menu bar that tells me if there are any updates available. I think it also shows a little pop up saying how many patches are available. Hopefully that will work for you.

---

