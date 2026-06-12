---
title: "can i just delete the linux ext3 partition without doing harm to my bootloader?"
date: 2006-01-13
forum: General Help
---

### Post by zahidism on 2006-01-13
As of now my laptop is running windows and linux.  I believe the hda order is windows then linux then a fat32 drive.  i would like delete and format the linux and fat32 partition to make it a whole windows hard drive again because im installing ubuntu on another computer.  my question is...wouldnt this seriously mess up the GRUB bootloader...??  i dont really want it there considering i want windows XP to load all the time...is there anyway to rewrite the master boot record w/ the windows one without actually reinstalling windows?

---

### Post by magnusbb on 2006-01-13
If the bootloader was installed to the MBR, this should not affect it.

---

### Post by psusi on 2006-01-13
Yes, it will blow away grub leaving the system unbootable.  You can fix that by booting from the windows install cd and dropping to a recovery console, then issuing the FIXMBR command.

---

### Post by zahidism on 2006-01-13
also, i cant seem to delete the linux partitions on live CD using gparted because it says that my linux swap is mounted (or in use...i dont kwno what that means)  any way around this?

---

### Post by psusi on 2006-01-13
sudo swapoff -a

Or don't bother using the livecd, just blow the partitions away from within windows.

---

