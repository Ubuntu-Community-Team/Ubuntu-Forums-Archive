---
title: "Starting computer.."
date: 2005-07-13
forum: Desktop Environments
---

### Post by sweetthdevil on 2005-07-13
Hi, i had a problem with my windows xp, so i formated and reinstall, but now when my laptop start, it doesn't give my the choice of starting ubuntu or xp.

I don't want to re install ubuntu so how can i fix the starting problem? :-?

---

### Post by az on 2005-07-13
You need to sneak back into your linux system and run 
grub-install


Assuming your linux partition is /dev/hda5 do this:

Boot the Ubuntu installer.  Make your way to when it detects all your disks and starts the partitioner.

CTRL-ALT-F2 to go into a console.

mount /dev/hda5 /mnt
chroot /mnt
grub-install /dev/hda
reboot.

Let me know if that works.

---

