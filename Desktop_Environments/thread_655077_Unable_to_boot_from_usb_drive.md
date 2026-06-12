---
title: "Unable to boot from usb drive"
date: 2007-12-31
forum: Desktop Environments
---

### Post by Abgrund on 2007-12-31
I made a (theoretically) bootable usb drive using these instructions:

[http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install/](http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install/)

The process appeared to be completed without problems, and there are certainly files on the drive, but the BIOS (Award Phoenix 6.00 GP) appears unable to recognize it. The first boot priority is set to USB-ZIP, and the BIOS **will **recognize any other usb drive and attempt (unsuccessfully) to boot from it, but it doesn't react to the Ubuntu boot drive at all, either as USB-ZIP or USB-HDD.

Windows recognizes only one partition on the drive (of 715M FAT), which it seems to have no problem reading.

Suggestions?

---

### Post by phidia on 2008-01-01
I think it might help you to look at the community docs [here]("https://wiki.ubuntu.com/Booting") Also[ this]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") community doc covers usb drive install and booting. Hope that helps.

---

### Post by Abgrund on 2008-01-02
fdisk reports that the flash drive has 3932 cylinders rather than 1024 and that this could cause problems with booting and partitioning software from other O/S's. Could this be a cause of the BIOS not recognizing the drive at all, while it recognizes smaller drives?

---

