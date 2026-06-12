---
title: "Cannot mount USB Drives"
date: 2009-02-21
forum: General Help
---

### Post by Bill Roberts on 2009-02-21
I have 2 USB devices, a thumb drive and an external hard drive that will not mount.  The message detail is "Cannot create mount directory".  I don't know how to create a mount directory for a usb drive.  They used to automount, but I disconnected them to move my system and when I reconnected them, this problem showed up.

Any help would be appreciated.

---

### Post by WaffleCode on 2009-02-21
Try going to the terminal and typing the following

*sudo mkdir /media/(desired-name)*
*sudo mount /dev/??? /media/(desired-name)*

??? == device system name, probably something like 'sdb1.'

Good luck.

---

### Post by Bill Roberts on 2009-02-21
It had something to do with moving the machine.  I shut down, removed both devices, booted then plugged them back in and all is well.

---

