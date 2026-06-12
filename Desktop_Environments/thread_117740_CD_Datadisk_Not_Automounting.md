---
title: "CD Datadisk Not Automounting"
date: 2006-01-15
forum: Desktop Environments
---

### Post by wacole on 2006-01-15
I have used Gnomebaker to produce a backup disk of my home directory.  Under 5.04 I was able to read this CD when placed in the CDROM drive; it automounted and appeared on Nautilus.

I am now using 5.10 and after a fresh update of my CD-RW backup disk using Gnomebaker the system does not "see" the CD when it is reinserted after Gnomebaker is finished writing the disk and has ejected it. [BTW I have installed the automount update that was distributed through Ubuntu last week or so.]

I should note that the system will automount audio CDs and play them and will automount the 5.10 install disk.  It will also see ISOs just fine.

Do I have an automount problem or a Gnomebaker problem or something else, please?

Clues would be most appreciated.

Thanks much, indeed.

---

### Post by wacole on 2006-01-23
Here's what I've found out in the past few days:

If I put an unused CD-RW in the CD drive, Ubuntu will automount it and properly identity it as CD-RW in the desktop icon.

If I put an unused CD-R in the CD drive, Ubuntua will automount it and properly identify it as CD-R in the desktop icon.

If I write to that same CD-RW with Gnomebaker, Ubuntu will _NOT_ automount it after the write is finished and I re-insert it into the CD drive.

If I write that same CD-R using Gnomebaker, Ubuntu _WILL_ automount it and properly identify it as CD-R in the desktop icon after it is reinserted in the CD drive.

In all cases the media is made by Memorex.

So, it appears that wherever the problem is - I can't tell if it's Nautilus or Gnomebaker - it has something to do with CD-RWs.

---

### Post by wacole on 2006-02-04
Have been able to mount a CD-RW created with Nero on another machine.  This clearly narrows the problem down to Gnomebaker.  Time to look for another Linux-based burner.

---

