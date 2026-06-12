---
title: "Stage 1 grub on usb"
date: 2006-08-28
forum: Desktop Environments
---

### Post by gary800 on 2006-08-28
I want to install grub stage 1 on the MBR of a USB key. The idea being that
I can boot from the USB that will point to a hard-drive that contains the menu.lst file. 

I can then reload the windows mbr to hard-disk and only boot to linux
when the usb key is available at startup. Effectively hiding linux.

Reading over the LPI guide from IBM, the instructions for installing grub
stage 1 is issuing the command "grub-install /dev/sda".

For me, this returns: “/dev/sda does not have any corresponding BIOS drive”.
I'd like to know if I'm heading in the right direction and if I anyone has tried this with success.

---

### Post by anaconda on 2006-08-28
If you have the grub installed to your hd, then you can copy it from hd:s mbr to your usb-stick by using dd-command
```

dd if=/dev/hda of=/dev/sda bs=1 count=446
```

assuming your hd is hda and that your usb-stick is sda

---

