---
title: "mount after umount"
date: 2011-04-04
forum: Desktop Environments
---

### Post by Mosabama on 2011-04-04
Hey,

Why cant I mount a flash disk or a CD after I umount it?

when I want to mount anything after I umounted I get this:

```

mount: can't find /dev/sdc2 in /etc/fstab or /etc/mtab

```

the only way is to remove the flash disk and insert it again to be mounted automatically.

---

### Post by ajgreeny on 2011-04-04
When a usb drive mounts automatically the mountpoint folder is made "on the fly", when you remove or unmount the drive that folder disappears.

You would need to know the /dev/sdx# and have a ready made folder to mount the drive and would then be able to do what you want.

Manual mount commands also need the filesystem type (vfat) and maybe other options to make them useful.
```
sudo mount /dev/sdb1 /media/mountfolder/ -t vfat -o iocharset=utf8,umask=000
```

---

### Post by areeda on 2011-04-04
> **ajgreeny said:**
> When a usb drive mounts automatically the mountpoint folder is made "on the fly", when you remove or unmount the drive that folder disappears.

You would need to know the /dev/sdx# and have a ready made folder to mount the drive and would then be able to do what you want.

Manual mount commands also need the filesystem type (vfat) and maybe other options to make them useful.
```
sudo mount /dev/sdb1 /media/mountfolder/ -t vfat -o iocharset=utf8,umask=000
```
Not quite you don't NEED that extra info for most filetypes on a USB or CD but you do need the mount point.

The error message reported no /dev/sdxx in fstab or mtab usualy means the form of the mount command was just "mount /dev/sdc1"  which would work if there was a corresponding entry in fstab.

For example:
```
jsa:~[7] mkdir usb
jsa:~[8] sudo mount /dev/sdc1 usb
[sudo] password for joe: 

```
Mounts a USB to the folder in my home directory.  

The one tricky thing is drive letter ("c" of /dev/sdc1) is not constant, it seems to change based on the order devices are recognized, I think.  My cdrom is usually sdb and first USB is sdc but I've seen them reversed.

The System->Disk Utility will mount and unmount removable media.

Joe

---

### Post by Mosabama on 2011-04-04
oh god I am sorry you are both right how did I miss that .. than you very much

---

