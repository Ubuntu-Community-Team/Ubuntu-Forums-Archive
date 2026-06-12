---
title: "need help to transfer my home directory to usb hdd"
date: 2007-05-06
forum: Desktop Environments
---

### Post by Panos on 2007-05-06
Hello all,

I would like to transfer my existing home directory(which is not in a separate partition)  to an external usb hard disk and have it mounted automatically at boot time. I have already copied my home directory to the disk, so all I want is the right fstab entry. I tried myself but I messed it up so I had to edit the fstab again to restore my desktop.

Thanks in advance.

Panos

---

### Post by benerivo on 2007-05-07
I would make sure the usb drive is recognised, by running gparted and checking that it is visible and formatted for linux, and noting the device name it uses (eg hdb1).

Then edit the fstab file to put in an entry for home. I think it should look something like this...

/dev/hdb1 /home ext3 umask=000  0 0

---

