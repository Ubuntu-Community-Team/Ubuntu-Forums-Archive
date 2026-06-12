---
title: "Can't mount anything"
date: 2005-08-04
forum: Desktop Environments
---

### Post by Event Horizon on 2005-08-04
I just installed Kubuntu along with Windows XP in dual-boot mode. Whenever I try to mount a partition (NTFS or FAT32) they both give me this error:

Error - Konqueror
Could not mount device
The reported error was:
mount: can't find /dev/sda* in /ect/fstab or /ect/mtab

Where * is the partition number. All the devices are listed in the "storage media" page, but cannot be mounted. But, the partition where kubuntu is installed IS mounted and can be accessed normally.

I'm a noob when it comes to linux, I'm probably missing something really obvious. Anyone have any ideas?

---

### Post by varunus on 2005-08-04
When you want to mount a disk in linux, you have two options.  Either root can mount it, or the partition can be added to the /etc/fstab file to allow all users to mount it.  (There are small exceptions with USB removable drives; Ubuntu includes a utility called pmount that lets those be mounted without root priviledges.  (Of course, that's Ubuntu, not sure about Kubuntu.))

For example, here's my /etc/fstab file:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro,user_xattr 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    umask=0222      0        0

```

You can see how I've mounted my windows partiton at the bottom there.  (This will also make everything in it automatically mount at boot unless the "noauto" option is written, as you can see with my /dev/hdc.)  Any drives you want to use, you can add there.  The ubuntu guide at [http://www.ubuntuguide.org](http://www.ubuntuguide.org) has information on how to mount windows drives.

---

### Post by Event Horizon on 2005-08-04
Thanks a bunch. Now here's a second problem:

What's the root password?


EDIT: Ok, so you type:

sudo passwd root

into the console, but it doesn't let me enter anything. None of my keyboard inputs work, except enter and escape and some others. Why is this?


God, I'm so new to all this.

---

### Post by varunus on 2005-08-05
OK, one thing about Ubuntu/Kubuntu is that there is no root password.  When KDE asks you for a root password, enter *your* password.

If you try to enable the root password (which I don't recommend, just use sudo and your own password, its safer) you need to type your own password, then the root's password.  It will stay blank in a terminal so other people can't see how long your or the root's password is.  Security feature, not a bug in your keyboard.   :)

---

