---
title: "Floppy on Xubuntu6.06 - Xfce"
date: 2006-08-21
forum: Desktop Environments
---

### Post by samuelb on 2006-08-21
Hi everybody!
I'm a beginner in .nix systems so I've some questions...

I use Xubuntu 6.06 (great!) with Xfce4 Desktop Environment version 4.3.90.2 (Xfce 4.4 BETA1)

How can I automatically mount floppy drive when I start a session?

In my fstab the last lane is
/dev/fd0 on /media/floppy0 type vfat (rw,noexec,nosuid,nodev)

If I thype in terminal
mount /media/floppy0  this works.

How can I automatically do this?

I tried this:
In /home/myfolder/ I created a file named "floppy" with the instruction 
mount /media/floppy0

Then i thyped
sudo crontab -e
and in the las lane I wrote
@reboot /home/myfolder/floppy 

This seem it doesn't work... Any suggestion?
Thanx. Samuel

---

### Post by orb9220 on 2006-08-21
Well first there are no lines in my fstab for floppy but the floppy shows up just fine in nautilus. One I don't think you mount a floppy until there is something in the drive to mount a disk.

Like the cdrom dosn't show on the desktop until you insert a disk then it get's mounted. If you insert a floppy and click on floppy it should read.

---

