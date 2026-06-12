---
title: "How to mount external usb drive?"
date: 2006-09-03
forum: Desktop Environments
---

### Post by wwuster on 2006-09-03
My .Trash folder somehow got messed up and when I tried to empty
/home/user/.Trash as root my system won't reboot anymore. I cannot boot into a
graphical interface anymore. But as root I can still see my data in /home/user.
I plugged in an external usb hard drive to the Ubuntu machine but can't find
how to mount it from a root console. Can someone tell me how? I'm planning to
copy my data and re-install Ubuntu.

Somehow my .Trash folder seemed to be connected to my home folder. Maybe there
was a symbolic link in .Trash to $HOME? I tried adding another user and copying
the data but it seems the system is pretty messed up because that has problems
too.

thanks,
William

---

### Post by mssever on 2006-09-03
Assuming the HD is formatted as ext3, do this:
```
mount -t ext3 /dev/sda1 /mnt
``` where sda1 is the device name. If sda1 doesn't work, try sdb1, etc.

The drive will be accessible at /mnt.

---

### Post by wwuster on 2006-09-04
The drive is fat32. I tried this:

mount -t vfat /dev/sda1 /mnt/external, etc, but I get the message

"mount: the special device /dev/sda1 does not exist"

How can I find what is the name of this external hard drive is?

William

---

### Post by xyz on 2006-09-04
> How can I find what is the name of this external hard drive is?
In a console, type:

```
sudo fdisk -l
```

---

### Post by Brandon.Viking on 2006-09-04
> **wwuster said:**
> The drive is fat32. I tried this:

mount -t vfat /dev/sda1 /mnt/external, etc, but I get the message

"mount: the special device /dev/sda1 does not exist"

How can I find what is the name of this external hard drive is?

William

```

sudo fdisk -l /dev/sda 

```

may help if the default device isnt the one your after. using "tail" and the "dmesg" command may help in identifing the drive id right after you plug it in.

Hope it helps.

---

