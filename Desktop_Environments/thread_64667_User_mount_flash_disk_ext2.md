---
title: "User mount flash disk ext2"
date: 2005-09-11
forum: Desktop Environments
---

### Post by yoloosis on 2005-09-11
Hi everybody !
I've got a 256 Mo flash disk with two partitions :
- a large FAT32 for exchanges
- a smaller ext2 for save vital informations like gpg keys, etc...

When I plug it, it's appearing in the media:/ with Konqueror. No problem with that. When I mount the FAT32 as a normal user, the result of the 'mount' command is correct, with a good uid, so I can write on it. But the ext2 partition is mounted as root (no uid informations on fstab), so I can't write on it...

This is the result on the 'mount' command, without option :
```

...
/dev/sda1 on /media/sda1 type vfat
(rw,noexec,nosuid,nodev,sync,quiet,uid=1000,gid=1000,umask=077)
/dev/sda2 on /media/sda2 type ext2 (rw,noexec,nosuid,nodev,sync)
...

``` 

How could I make why ext2 partition writable by a normal user without tweaking /etc/fstab as root ?

Thank you a lot !

---

### Post by mlomker on 2005-09-12
[QUOTE=yoloosis]How could I make why ext2 partition writable by a normal user without tweaking /etc/fstab as root ?
[/QUOTE]

The fstab file can dictate who is allowed to mount the drive, not who can write to it.

**chmod 777 /media/sda2**

---

### Post by yoloosis on 2005-09-12
Thank you !
But as you know, the entry in fstab in written AFTER i've clicked on the disk icon in media:/ in Konqueror. In the options, you can see that this partition is mounted with the rights of the user who mounted it (check the uid=1000,gid=1000,umask=077 options on the line). Somewhere in the system, there is a config file who say "The one who mount this partition mount under his own uid and gid with umask=077".

What is this config file ? ;-)

---

### Post by mlomker on 2005-09-12
[QUOTE=yoloosis]What is this config file ? ;-)[/QUOTE]

Why don't you just add the line that you want to /etc/fstab?  Having hotplug automatically create the entry is a convenience, not a necessity.

---

### Post by yoloosis on 2005-09-12
> Having hotplug automatically create the entry is a convenience, not a necessity. 
You're right ! But :
1) I think an all automatic and sensible mount will make beginners very very happy in the future versions of (K)Ubuntu
2) I'm curious about what I can do with HAL, hotplug, udev and so on...

Thanx to answering me mlomker, in about all topics who involved me ! Even if my english is not really good...

---

### Post by mlomker on 2005-09-12
You can change the 'mode' value on the appropriate line in /etc/udev/udev.rules.

```

# permissions for USB/FireWire block devices
BUS="scsi", KERNEL="sd[a-z]*", PROGRAM="/etc/udev/scripts/removable.sh %k", RESU
LT="1", NAME="%k", MODE="0660", GROUP="plugdev"
BUS="usb", KERNEL="ub[a-z]*", NAME="%k", MODE="0660", GROUP="plugdev"

```

I think you just have to change the default 0640 to 0660, as above.

[Documentation is here.](http://www.reactivated.net/writing_udev_rules.html)

---

### Post by yoloosis on 2005-09-12
Thank you, I'm thinking your a kind of guru...!

And I'll think I'll start to play a little bit with my udev's rules...

---

### Post by mlomker on 2005-09-12
[QUOTE=yoloosis]And I'll think I'll start to play a little bit with my udev's rules...[/QUOTE]

Not really, I'm just reading the documentation and learning.

It looks like this isn't what you're looking for.  The Udev service creates the entries under /dev, so this isn't what we want to change.

It looks like HAL calls pmount and pmount is what creates the directory under /media.  What you'd want to figure out is what script calls pmount...then you'd add a command that would **chmod 777** the directory that pmount creates.  The problem is that pmount creates the device as owned by root and not writable by users...and that can't be easily changed, apparently.

---

### Post by yoloosis on 2005-09-12
The problem is perhaps elsewhere : it's good with FAT32, because in the fstab, uid  gid of the user who clicked on the icon are wrotten. Not in case of ext2. It should be possible to write uid and gid even in case of ext2, isn't it ?

---

### Post by dbw on 2006-12-14
For external devices, that are not in the FSTAB, you can use:
```
pmount sda1 usb_disk
```
This will mount /dev/sda1 as /media/usb_disk, and you are the owner.  unmount with "pumount".  There are three critera for pmount to work:
1. device must not be in fstab.  (so comment out those lines...)
2. device must not already be mounted.   (um.  duh)
3. folder /media/usb_disk must not exist, as pmount CREATES this folder.  (so either kill your older folder as root, or choose a new folder name)

Does that work?

---

