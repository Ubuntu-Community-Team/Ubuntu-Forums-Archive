---
title: "floppy drive"
date: 2004-10-27
forum: Desktop Environments
---

### Post by smoothrt on 2004-10-27
After playing around with this I have got it so ubuntu finally recognizes and mounts my floppy drive on bootup.  The problem is, if I read a diskette, it gets mounted and placed on my desktop, and becomes impossible to remove the icon from my desktop, with or without the disk in my computer.  It just comes back with an error message saying unable to unmount and the details say that the device is busy.  I have the following line in my /etc/fstab file:

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Is there something I can change here so that doesn't happen, and I can remove the disk from the hard drive from the desktop without having to reboot?  Thanks.

---

### Post by jdong on 2004-10-27
I can't reproduce this issue. What did you do after mounting the floppy? Browse it? Open a document with {application x}?

Did you close all windows browsing the floppy, and close all consoles that are in the floppy's directory?

If so, then congrats, you found a bug. File it.

---

### Post by FLeiXiuS on 2004-10-27
**Fixing Mount Points on Desktop**
There is an option in the gconfig application under:

Applications > System Tools > Configuration Editor

navigate to 

/apps/nautilus/general or desktop

It's one of those, I'm not booted into Ubuntu as I am at work.  There should be a checkbox there.

---

### Post by jdong on 2004-10-27
[QUOTE=FLeiXiuS]**Fixing Mount Points on Desktop**
There is an option in the gconfig application under:

Applications > System Tools > Configuration Editor

navigate to 

/apps/nautilus/general or desktop

It's one of those, I'm not booted into Ubuntu as I am at work.  There should be a checkbox there.[/QUOTE]
 yeah, but that shouldn't cause a floppy to fail to unmount. I always right-click the floppy icon on my desktop and choose "Unmount".

---

### Post by FLeiXiuS on 2004-10-27
Of course, I was just giiving you the fix for desktop mount points.  Have you checked```
du -h
``` to see if its mounted and if so where.

It may just be the icon frozen on the desktop.

---

### Post by DCuser on 2004-10-29
I am also having a number of floppy drive problems.  I can't use the icon on the "Computer" "Disks" menu normally.  It gives a message that it doesn't recognize the format of the disk (it is msdos).

Then, I can go into a terminal and type 

sudo mount -t msdos /dev/fd0 /media/floppy0

and it mounts.  This has issues when I try to use it with programs in my normal user-id though.

I can type 

sudo umount -l /dev/fd0

to unmount.  The -l is for a "lazy" unmount, which works everytime. (Will solve the above-mentioned problem.)

THEN, once I have unmounted in the root level, I can use the top-bar "Computer", "Disks" and select "Floppy 1".  At this point the floppy is properly recognized under my normal user-id.  It works, but this is not exactly user-friendly.

I'm using a Dell Dimension.  Could that have something to do with it?  I have to run "nodma", which might change some factor somewhere (at install, the system would not see my CD-Rom without the "nodma" option on the original "linux" command, and even then it took a few tries).

---

### Post by Orcrist on 2004-12-01
I have this same problem when I try to read or format a floppy.  I go to the 'disks' menu in gnome, mount it, format it, then when I go to unmount I get the 'device is busy'

Using a lazy umount (posted above) works for me, but as that person said, is not very user-friendly.

I also am on a Dell Dimension (4600 series).  Seems to be a common thread here, perhaps?

---

### Post by BWF89 on 2004-12-01
I have the Ubuntu live CD. How do I copy something to a floppy? I saw a file called "floppy" and I clicked on it and it said something about having to be logged in as root...

---

### Post by Gnobian_Ken00bie on 2005-01-07
I encountered a similar problem with unmounting floppies in Ubuntu... and I searched the web, finding this thread and similar ones in other forums - but with no clear answer, apart from using the commandline: sudo umount -l /dev/fd0

The problem is that, while I have convinced family members to switch to GNU/Linux and Ubuntu is much loved, there is not so much enthusiasm for the commandline. Also, they are not all in the sudo-ers group.

But I found the source of the problem and I am almost certain that this will resolve smooth's difficulty and my own. Clearly, there is a process not letting go of the floppy.
But looking at the processes list gives no clue what it might be. And many are not encountering the problem, including apparently many of the more experienced users.

The answer is this: by default, Ubuntu opens a window when you mount removable media. But it opens it on the desktop of EVERY user who is logged in. If I am correct then only a user who is logged into one account while others are also logged in will encounter this. That explains why support hasn't been able to reproduce the problem.

You would have to log in to each open account and close the browser window on each desktop before you could unmount the disk.

An alternative is this:
Applications-->Configuration Editor-->desktop-->gnome-->volume manager--> remove the checkmark after autobrowse

Then a browser window won't open automatically  when you mount a disk and  more importantly it won't be open on the desktop of every other user that is logged in.

This is my first time reporting on a bug or a problem, let alone offerring a solution. I hope I got this right.

---

