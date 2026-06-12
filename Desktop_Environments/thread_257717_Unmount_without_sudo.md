---
title: "Unmount without sudo"
date: 2006-09-14
forum: Desktop Environments
---

### Post by Starlyth on 2006-09-14
summary: run umount without a password, but only for one device.

Explanation:
I am currently using [TrueCrypt]("http://www.truecrypt.org") on a microdrive, which is plugged in through a USB card reader.  I would like to be able to press a button which will (1) unmount my TrueCrypt volume, (2) unmount the microdrive. 

I already have the button to unmount the TrueCrypt volume (command: truecrypt -d), and it works fine.  I would like to maintain that ease with unmounting as well.  Yes, I can just right click the icon on the desktop, select unmount, and it is.  I would like to avoid that, if I can.

However, after doing some searching via Google, looking through man, and at rute's unix page, I'm at a loss.  I think that adding to the sudoers is what I'm looking for, but I'm not sure.  I only want to unmount this microdrive (mounted at /media/microdrive) without a password.  I don't want to be able to do it on anything else without a password.

Any thoughts?:-k

---

### Post by howardepgco on 2006-09-14
Just a suggestion and I don't know if it will help you, look in <system> <administration> <disks> you may find what you need to do in there.

---

