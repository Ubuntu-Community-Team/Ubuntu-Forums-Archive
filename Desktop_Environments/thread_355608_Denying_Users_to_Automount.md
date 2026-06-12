---
title: "Denying Users to Automount?"
date: 2007-02-07
forum: Desktop Environments
---

### Post by ulmi on 2007-02-07
Hi there,

How can I disable the automount feature of g-v-m for a specific user?
I don't want the user to be able to access any usb/cdrom -media.
I'm running Ubuntu 6.10

---

### Post by dannyboy79 on 2007-02-07
well for your cdrom, you would put a line like this in your fstab:
/dev/hda        /media/cdrom0   udf,iso9660 noauto     0       0

notice the user or users option is missing.

as far as making it so usb devices can't be mounted by anyone, that I am not sure about as pmount handles them and according to man pmount, it's going to get mounted The   device   will   be   mounted   with    the    following    flags:
       async,atime,nodev,noexec,noauto,nosuid,user,rw
if the following criteria ARE met:
Â· device is a block device in /dev/

       Â· device is not in /etc/fstab (if it is, pmount executes  mount  device
         as the calling user to handle this transparently)

       Â· device is not already mounted according to /etc/mtab and /proc/mounts

       Â· if the mount point already exists, there is no device already mounted
         at it and the directory is empty

       Â· device   is   removable   (USB,   FireWire,   or   MMC   device,   or
         /sys/block/drive/removable is 1) or whitelisted in /etc/pmount.allow.

       Â· device is not locked

so I suppose you could add fstab entries for sda1, sda2, sda3 blah blah blah for usb devices and make them have the noauto and make sure they DON'T have the user or users option. other than that, not sure.

---

### Post by dannyboy79 on 2007-02-07
this also has a bunch of great info

[http://www.die.net/doc/linux/man/man1/gnome-mount.1.html](http://www.die.net/doc/linux/man/man1/gnome-mount.1.html)

---

### Post by ulmi on 2007-02-07
thanks, this looks like it could work.
But I hoped to find a clean way to only deny the (auto)mounting for specific users.
Isn't there some sort of Permissions/Authorization for g-v-m/pmount?
Looking at the manpages/google I haven't found anything so far.

---

