---
title: "After upgrade, can't unmount firewire disks."
date: 2007-05-11
forum: Desktop Environments
---

### Post by jml75 on 2007-05-11
Hi all,

So like I pointed in the title, since my update from 6.10 to 7.04, I can no longer unmount my firewire drives in Gnome.

When I plug the drive in the firewire port, it mounts on Gnome's desktop and I can use the disk properly.

But when I right click on the disk and choose to eject the drive, the icon disapears, I get a popup message saying that it is impossible to eject the volume and after that the icon reapears.

Of course, I can unmount it as root from the command line but I'd rather solve this permission issue...

Thanx for your help!

---

### Post by ozorba on 2007-05-11
Have you tried to unmount the drive with 'sudo umount' command?

# sudo umount /media/firewire

where /media/firewire is the directory where the firewire disk is mounted.

---

### Post by deelerious on 2007-05-11
I get the same thing; ejecting any external drive, USB or Firewire, cannot be completed from Nautilus with the same message jml75 described.

Unmounting from the terminal works fine.

---

### Post by roboguy on 2007-05-13
Count one more with this problem!

---

### Post by th0mas on 2007-05-14
same problem here...

---

### Post by superFerra on 2007-06-26
me too!!
I'm running  Fiesty (fresh install)  and i can't unmount my firewire disk (WD My Book) via Gnome interface.
Any idea/suggestion??

TIA

---

