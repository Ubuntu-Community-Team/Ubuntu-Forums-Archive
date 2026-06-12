---
title: "Need help changing USB disk desktop display."
date: 2006-06-05
forum: Desktop Environments
---

### Post by arsenic23 on 2006-06-05
I posted the following over in the beginner forum but got no replies:

> Well, I finally got around to beginning my round of dapper installations, and so far I'm digging it. Right now though, I have one big annoyance that I haven't got figured out, and I figured I'd post it before I go to sleep.

I have a USB hard drive with 2 partitions, a 323gig NTFS, and a 48gig ext3. When I'd plug them in using breezy it would show "323.8 GB Volume" and "48.8 GB Volume" under them. 

Now on my Dapper install I see their location names under them, so that whichever one is mounted in /media/usbdisk is called "usbdisk" while the other is "usbdisk-1" and they'll switch mount points the same as when I was using Breezy.

Is there any way to get them back to where they were showing the sizes?
[http://www.ubuntuforums.org/showthread.php?p=1095063#post1095063](http://www.ubuntuforums.org/showthread.php?p=1095063#post1095063)

I could really use some help with this as not being able to tell the difference between the partitions on my drive is 10 kinds of liquid annoyance.

( I dislike double posting like this, but I figured there may be someone here who doesn't often visit the beginner forum, what could help me out. )

---

### Post by lean on 2006-06-05
HAL which is the subsystem that takes care of recognising your hardware, has a lot of support of recognising the serial number of your harddrive. But there is still a lot of work in getting it to work with the desktop.

Your problem is not a serious issue, but developers are aware of it. I think it will be fixed in the next release, or in the next after that (so 4-10 months).

---

### Post by arsenic23 on 2006-06-05
umm... I really don't need the machine to know what the drive or partitions it's mounting are, I just need to change what Gnome displays under their icons on my desktop.

I'd like to make it display the size of the drive instead of the name of the place it's mounted.  ( Like it was in Breezy. )

---

