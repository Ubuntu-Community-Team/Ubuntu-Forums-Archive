---
title: "Problems with copying files on USB with Nautilus."
date: 2007-04-22
forum: Desktop Environments
---

### Post by rapasoft on 2007-04-22
The main problem is, when the USB disk is connected it is mounted by gnome-vol.-man - the files are viewable, but when i try to copy something (i.e. 100M files) the progress bar shows that the files are copied within several seconds (it is imposible on USB1.1) but then i still can't unmount the device, because the files are being transferred to it. I suggest that it may be combination of wrong USB settings (where?), because i have same problem with Thunar and Nautilus...

---

### Post by Pobega on 2007-04-22
Use the command line and see what happens.

Make sure to close all of your nautilus windows with the USB drive, and run:

umount /dev/sda*

Replace the asterisk with whatever your USB thumbdrive shows up as.

---

### Post by rapasoft on 2007-04-22
ok, so now i umounted it, but it seems, that i've cancelled the file transfer... i want to now why nautilus gives me inappropriate information (because when I wait for a while, i can umount it normally and the files are on USB stick).

ok, i'm a ubuntu newbie,... which config files should i post?

---

### Post by rapasoft on 2007-04-23
i searched couple of forums and the problem seems to be in that USB disks are mounted with sync option. when i try to eject it, it pops up a message that data are being transfered... but i want to know a progress of this transfer! how?

---

