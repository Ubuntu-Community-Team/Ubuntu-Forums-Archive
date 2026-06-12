---
title: "External disk: You are not privileged to mount this volume."
date: 2009-05-11
forum: General Help
---

### Post by _sAm_ on 2009-05-11
On Ubuntu 9.04 Desktop(64b)

When I plug in my external harddrive(USB disk with ext3) I get the error: You are not privileged to mount this volume.

I have added the disk in /etc/fstab like this;
/dev/disk/by-uuid/7142a339-a707-4535-8908-e9d37ca90c87 /media/backup ext3 defaults 0 0

sudo ls -l gives(in /media/;
drwxr-x--- 10 sam  sam  4096 2009-05-07 16:49 backup


Under; System&#8594;Administration&#8594;Users and Groups&#8594;"your user"&#8594;Properties&#8594;User Privilegies&#8594;Acces external storage device automaticlly is set on for my user. Same under /etc/group(after plugdev).

If I run the command sudo mount -a it will mount and work as it should(my user can then use it).


What am I doing wrong?

---

### Post by logos34 on 2009-05-11
You might try removing the fstab entry and using automount:

> [Automounting]("https://help.ubuntu.com/community/Mount/USB#Automounting")

Mounting

By default, storage devices that are plugged into the system mount automatically and place an icon on your desktop, often called "disk" and as more drives are added, you can get "disk-1" and so on.

To change the automatic mount point and label of external drives, see [RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive").

---

### Post by _sAm_ on 2009-05-11
No, then rsync commands(via alias) will fail - I need to mount the disk as /meda/backup each time I mount it.

This used to work before.

---

