---
title: "Gnome Panel Disk Mounter shows extra floppy drive, neither shows on desktop."
date: 2007-02-11
forum: Desktop Environments
---

### Post by Bastanteroma on 2007-02-11
My pc has a floppy drive which I rarely use, but which I'd prefer to not unplug (the case is broken and difficult to open up and put back together).  The Disk Mounter panel applet shows two floppy drive icons when there is no disk in the drive.  I'd prefer it to behave with floppies like it does with cd drives, only showing up when I put a disc in.  I commented out the floppy line in etc/fstab and one of the floppy icons disappeared, but there is still one on the panel, most likely useless without that line in fstab.  Mounted volumes show up on the desktop fine, only when they are actually present.

---

### Post by jourdanritchey on 2007-02-16
I had the same issue.  A "Floppy Drive" and a "Floppy 1" in the Gnome Disk Mount applet.  Seems as though commenting out fstab is all that's needed, as either:
- HAL picks it up without fstab, or
- the UDEV rules make it exist

I can't know the why of it without spending more time than I want to, but taking the line out of fstab does the trick.  I wonder if I take the lines out for my cdroms whether those will still be picked-up by Gnome...

BTW, the floppy will always appear - it simply can't be dynamic like the CD drives.  It has to do with how the hardware works.

---

