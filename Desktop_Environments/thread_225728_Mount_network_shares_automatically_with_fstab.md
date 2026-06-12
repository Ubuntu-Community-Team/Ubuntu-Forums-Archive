---
title: "Mount network shares automatically with fstab"
date: 2006-07-30
forum: Desktop Environments
---

### Post by mudra on 2006-07-30
I am trying to mount a network share automatically by adding a line to my fstab. I have tried a couple of guides, but I am getting nowhere. I can do the mount successfully from the command line.

>  mount -t smbfs -o credentials=/root/.smbcredentials //192.168.0.1/Primary /media/backup/

When I add the following to my fstab it doesn't work.

> //192.168.0.1/Primary /media/backup smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0


Any advice would be greatly appreciated.

Mudra:confused:


EDIT: I was trying to mount using umount :!: NOT mount !!!!!;)

---

### Post by Abhi Kalyan on 2006-11-06
> **mudra said:**
> I am trying to mount a network share automatically by adding a line to my fstab. I have tried a couple of guides, but I am getting nowhere. I can do the mount successfully from the command line.



When I add the following to my fstab it doesn't work.



Any advice would be greatly appreciated.

Mudra:confused:


EDIT: I was trying to mount using umount :!: NOT mount !!!!!;)
Been seraching for the same thing for a long time.
No catch yet. Will keep you posted as and when some thing turns up

---

### Post by Abhi Kalyan on 2006-11-06
> **mudra said:**
> I am trying to mount a network share automatically by adding a line to my fstab. I have tried a couple of guides, but I am getting nowhere. I can do the mount successfully from the command line.



When I add the following to my fstab it doesn't work.



Any advice would be greatly appreciated.

Mudra:confused:


EDIT: I was trying to mount using umount :!: NOT mount !!!!!;)
xsmbrowser
havnt tried it out, but some say it works fine for mounting win directory's.

---

