---
title: "GNU alternative for Norton Ghost"
date: 2005-10-22
forum: Desktop Environments
---

### Post by nocturn on 2005-10-22
Is ther a free program that can more-or-less do what Norton Ghost does?
I would like to use it for both Linux (Ext3/Reiser) and Windows XP drivers.

---

### Post by davmac on 2005-10-22
Have you had a look at Partition Image ([http://www.partimage.org/](http://www.partimage.org/))?

Hope this helps,

Dave Mac

---

### Post by bonzodog on 2005-10-22
hrm...have a look at this:

[http://freshmeat.net/projects/g4l/](http://freshmeat.net/projects/g4l/)

Ghost for linux...still in beta.

---

### Post by zekolas on 2005-10-22
I have used Partition Image several times and have been very happy with it. I have used it both for linux images and winxp images, it works with NTFS file systems as well. 

It is not as user friendly as ghost, but it is free and does a very good job. However I believe it will only do one partition at a time, and not a whole drive(that may contain multiple partitions).

---

### Post by jeremy on 2005-10-22
I have also used partimage for cloning/backup and like it a lot, I run it from a knoppix cd.
Bonzo dog, have you used g4l, have you any idea how reliable it is?

---

### Post by SickTwist on 2005-10-22
In addition to Ghost for Linux and Partition Image, there is also [Clonezilla]("http://clonezilla.sourceforge.net/") (Linux utility that offers multicasting similiar to  Symantec Ghost Corporate Edition®) and [Ghost for Unix]("http://www.feyrer.de/g4u/") (runs from bootable CD or two floppy disks).

Also, Norton Ghost is compatible with *some* Linux filesystems (although I can't remember which ones, ext3 I think). However, Norton Ghost can run in a special bit-for-bit copy mode that is compatible with *any* filesystem and *any* OS. (This comes at the expense of taking up more disk space for the images.) So, you could also use Norton Ghost itself with Ubuntu if the other options do not work out for you.

Incidentally, the [Radified Guide to Norton Ghost]("http://ghost.radified.com/") is an excellent reference for using Norton Ghost if you need one.

---

