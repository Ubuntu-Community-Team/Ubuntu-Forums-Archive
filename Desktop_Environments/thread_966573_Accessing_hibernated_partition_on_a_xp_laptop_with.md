---
title: "Accessing hibernated partition on a xp laptop with ubuntu"
date: 2008-11-01
forum: Desktop Environments
---

### Post by Sefi on 2008-11-01
My mate has been having some trouble with his laptop.
The backstory:
His laptop went into hibernate, and now whenever he tries to boot it just comes up with the flashing cursor before loading xp and then hangs there.
We've tried loading the xp install from the cd but it just errors and restarts.
So now we've decided to try to use ubuntu to get his data off the 160 GB drive and then just reformat and put on either ubuntu or xp again.
Now our problem is trying to access the drive but obviously it wont mount properly in Ubuntu.
How can i gain access to it? I have already tried using the command:

sudo mount -t ntfs-3g /dev/sda1 /media/sda1/ -o ro,force

(i had tried without the sudo prefix before but apparently this lets it run as a root user)
but it just says "fuse: failied to access mountpoint /media/sda1/: No such file or directory"
My questions is what command should i be putting into the terminal to mount the drive?

If it helps its an old toshiba with a 160 GB internal HDD in it now, and we've been running Ubuntu from a live CD.

---

