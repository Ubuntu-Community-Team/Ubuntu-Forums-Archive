---
title: "Why is USB-disk write delayed?"
date: 2006-08-19
forum: Desktop Environments
---

### Post by Mazin on 2006-08-19
I find that when I'm using external usb disks, everything tends to work except for one weird behavior.  KDE will automatically mount it to sda1 (or similar), show the icon, pop up the dialog asking me what to do and everything.  The thing is, when I *write* to the thing, like copying a file, the usb drive shows some activity (then stops), and KDE shows that the file is there **BUT** it's not really.  If I pull it out then, and plug it back in, the file is gone.  When I unmount it (right-click icon > unmount) it, the unmount dialog comes up and stays for a while, _while it's writing the actual data to the disk_.  Then when the real data's finally written, the unmount dialog goes away and it's unmounted.

Why?  And how do I make it not do that?

---

### Post by ajgreeny on 2006-08-19
This is all due to the sync command in the lines in fstab, isn't it?  Though, of course, your external usb drives are not shown in fstab anyway but dealt with by pmount, I think.

The problem is the same with floppy disks, if you have one on your machine, unless you specify "sync" in the fstab line for floppy.  I'd be very interested to know how to deal with this problem for usb disks or usb flash drives as the situation is the same with them.

---

### Post by meng on 2006-08-19
I've heard this actually prolongs the life of your USB drive, by reducing the number of writes to one per plug-in. Hence the importance of unmounting before unplugging.

---

### Post by ajgreeny on 2006-08-19
Yes you are right, but I would still like to know as if it was a proper spinning external, disk, not a flash drive it would be good to move files immediately.  Anyway, I'm just curious how to do it.

---

### Post by kevpatts on 2007-07-31
I need to know how to disable this feature for removable drives. As they're removable they're not in my fstab. If I right click on the volume, click properties, the "volume" tab and then Settings I can set mount options. What should I put in here to turn off delayed write? (using feisty)

---

### Post by Gwasanaethau on 2007-08-06
I'm having the opposite problem - I used to get messages after I ejected a USB drive reminding me not to remove it until Ubuntu had finished writing to it and no a don't get them any more. Can anybody tell me how to get them back? I miss that warm, fuzzy feeling I used to get knowing that Ubuntu had completely written everything to the drive! :lol:

EDIT: It's OK now, it seems to have fixed itself&#8230;

---

