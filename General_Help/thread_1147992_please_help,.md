---
title: "please help,"
date: 2009-05-03
forum: General Help
---

### Post by bpkorol on 2009-05-03
a few months ago my laptop died but I managed to recover the hard drive, I have attached my old hard drive to my current computer via a  "rocket fish 2.5"SATA hard drive enclosure kit" I bought at futureshop but I want to wipe it and put Ubuntu on it so i can vista on one hard drive and Ubuntu on the other, how can I do this?

my PC currently has windows vista.
the portable hard drive) has Ubuntu on it but due to my horribleness at using the terminal i managed to mess it up pretty badly and I just want to start from scratch.

---

### Post by codeseer on 2009-05-04
> **bpkorol said:**
> a few months ago my laptop died but I managed to recover the hard drive, I have attached my old hard drive to my current computer via a  "rocket fish 2.5"SATA hard drive enclosure kit" I bought at futureshop but I want to wipe it and put Ubuntu on it so i can vista on one hard drive and Ubuntu on the other, how can I do this?

my PC currently has windows vista.
the portable hard drive) has Ubuntu on it but due to my horribleness at using the terminal i managed to mess it up pretty badly and I just want to start from scratch.

Just download the Ubuntu Live CD and restart the system, booting from the CD, when you get to about step 4 you'll want to do the 'manual partitioning' and be sure you select the proper drive, then set yourself a swap partition to the size of your RAM and a root (/) partition to the rest of the drive. Ubuntu should automatically handle the recognition of Vista being installed and place it on the Grub boot menu for you.

---

### Post by logos34 on 2009-05-04
> **codeseer said:**
> Ubuntu should automatically handle the recognition of Vista being installed and place it on the Grub boot menu for you.

It will indeed detect windows and add menu.lst boot entry, but it will also overwrite the vista bootloader on the internal hdd with grub, rendering your computer unbootable if the external usb is detached (because grub will be looking for the boot files on the usb).

So you might want to do it [this way]("http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/") so that grub goes on the MBR of the usb hdd rather than the internal (shouldn't be too much of a hastle to open up the lappy to disconect the hdd).

(the tut is applies to usb stick and usb-enclosed hdd)

---

