---
title: "Using Ubuntu to recover data off Windows drives"
date: 2009-04-15
forum: General Help
---

### Post by Blade_Jones on 2009-04-15
Anyone know about what Ubuntu can and can't do when recovering data off of a Windows system drive that won't start?  I've done some testing using an Ubuntu Live CD to migrate data, and it appears to bypass administrator folder privileges, encrypted files, "read only" files, and files with enormous file names. Any one of these things would otherwise HALT a data recovery using Windows copy and paste. Is there anything that can halt a data recovery using Ubuntu? 

After doing the "documents and settings" data backup off of a failing Windows system hard drive to an external USB drive, I reformatted the failing system drive with a new Windows installation, booted it with my Ubuntu Live CD, and then attempted to migrate the data back. Now all of a sudden the USB drive was "locked" and inaccessible. What could have caused this?  I wound up using Windows' XCOPY command to migrate the data onto the new Windows installation, and that worked fine.

---

### Post by night_fox on 2009-04-15
Data on a hard disk drive cannot possibly stop linux from being able to see or edit it. (definitely if you act as root) Linux transcends the permissions on a filesystem. So you can copy what you like provided you havent destroyed the filesystem through bad partitioning.

---

### Post by codeseer on 2009-04-15
What did you use to migrate the 'documents and settings' folder to the USB disk? I'd probably use rsync in recursive mode.

---

### Post by Blade_Jones on 2009-04-16
Can this "rsync" be run from a live CD?

> What did you use to migrate the 'documents and settings' folder to the USB disk? I'd probably use rsync in recursive mode.
Physically I used an IDE to USB convertor. I didn't use any software. Just a simple copy and paste. 

I still would like to know what was locking the USB drive when I tried to open it with Ubuntu. Again it transferred fine with Windows XCOPY.

> So you can copy what you like provided you havent destroyed the filesystem through bad partitioning. 
I guess what you're saying is that the only thing that's gonna stop Linux from copying is something major like a corrupted file system. 

Seems to me that if preserving attributes like encryption, permissions, and "read only" are not required then Ubuntu is the sure fire way for backing up customer's data. Right?

---

### Post by codeseer on 2009-04-16
Yes, rsync can be run from the Live CD. If you want something more graphical, you might want to look at these:

[http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage")
[http://www.howtoforge.com/back_up_restore_harddrives_partitions_with_ghost4linux]("http://www.howtoforge.com/back_up_restore_harddrives_partitions_with_ghost4linux")

However, rsync is great and gets the job done.

---

### Post by Blade_Jones on 2009-04-16
> [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://www.howtoforge.com/back_up_re...th_ghost4linux](http://www.howtoforge.com/back_up_re...th_ghost4linux)
Seems like these programs are cloning programs for imaging healthy drives that have no boot problems.  I'm happy with the freeware XXclone for drive imaging. 
For my purposes I need to back up just docs and settings (or "users" folder in Vista) JUST IN CASE their Windows system is damaged beyond repair, and I have to reinstall Windows and remigrate their docs and settings data only.

Does Rsync come bundled with Ubuntu on their LIVE CD?  Or must Rsync be run as a 2nd live CD?  Or must the two be merged into an ISO file and then burned to a new live CD?

---

### Post by codeseer on 2009-04-16
> **Blade_Jones said:**
> Seems like these programs are cloning programs for imaging healthy drives that have no boot problems.  I'm happy with the freeware XXclone for drive imaging. 
For my purposes I need to back up just docs and settings (or "users" folder in Vista) JUST IN CASE their Windows system is damaged beyond repair, and I have to reinstall Windows and remigrate their docs and settings data only.

Does Rsync come bundled with Ubuntu on their LIVE CD?  Or must Rsync be run as a 2nd live CD?  Or must the two be merged into an ISO file and then burned to a new live CD?

It comes on the Live CD.

---

### Post by Blade_Jones on 2009-04-18
Actually I just did some testing. Ubuntu actually only copies folders (and files within) without regard for user permissions, including administrator files. It would NOT copy encrypted folders.  It may not copy read only folders. Not sure about that. I'll have to do some more testing.

---

