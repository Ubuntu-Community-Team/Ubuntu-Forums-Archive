---
title: "permissions for usb key drive"
date: 2005-04-14
forum: Desktop Environments
---

### Post by Alexander Kirillov on 2005-04-14
Does anyone else have this problem?
When I plug in USB memory key (aka disk-on-key, aka thumbdrive), formatted as FAT, it gets automounted. However, all files get permission 700 (rwx------), which is not what I want. Anyone has any idea where it comes from?

I use default umask 022, so newly created files in my own directory have permissions rw-r--r-- (which is exactly what I want). I looked at /etc/udev/udev.rules, which contains lines like 

```
# permissions for USB/FireWire block devices
BUS="scsi", KERNEL="sd[a-z]*", PROGRAM="/etc/udev/scripts/removable.sh %k", RESULT="1", NAME="%k", MODE="0640", GROUP="plugdev"
BUS="usb", KERNEL="ub[a-z]*", NAME="%k", MODE="0640", GROUP="plugdev"

```
but as you can see, it has mode 640, not 700. So where does this funny permission comes from??

---

### Post by accuser on 2005-04-15
I may not be right, as I haven't tried this myself so if anyone knows better, please correct me.

The file and directory permission bits available are specific to the underlying filesystem format. Ext2 and Ext3 for example support the full set of permission bits, but FAT does not. FAT only supports read-only bit, so files are automatically readable and executable (r-x) and can be either writable (-w-) or not, depending on the read-only attributed of the files in question.

The permissions you have stumbled across are for the block device itself, and not the files stored on it.

Have a look at options available for mounting FAT drives to see if this helps.

---

### Post by Alexander Kirillov on 2005-04-15
[QUOTE=accuser] FAT only supports read-only bit, so files are automatically readable and executable (r-x) and can be either writable (-w-) or not, depending on the read-only attributed of the files in question.
[/QUOTE]

I know that FAT does not support permissions in UNIX sense. However, I'd expect that the reasonable thing to do in such situation would be to give the files the same permissions as for newly created files - as determined by umask, instead of making them automatically readable and executable (r-x) .  This is the way it worked for me in Warty, in Fedora, and elsewhere (same files, same thumbdrive). I wonder if it is a intentional change, or a bug I uncovered. 

For practical purposes, having files executable by default means that whenever I click on one, I get the dialog "do you want to see the file or run it?" I know I can get rid of it, but I am still annoyed...

Does anyone else see the same permissions, or it is me only?

---

### Post by SilvioTO on 2005-04-16
I have the same problem; when I try to delete files on usb stick, message tell me that the disk is read only. If I try to write, message tell me that permission are insufficient.  :???:

---

### Post by SilvioTO on 2005-04-16
I find one cause; in my case is happened that before I format and install new Hoary, I saved my data with Warty on this usb stick. I format my usb stick and now work well.

---

