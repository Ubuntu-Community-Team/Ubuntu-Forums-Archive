---
title: "Error of sorts trying to force open an ntfs internal drive."
date: 2008-12-18
forum: General Help
---

### Post by Viveck on 2008-12-18
Hello,

My laptop crashed and I'm trying to access my internal HD partitions but I can't mount because I get the "Cannot mount volume" error which is fine, I expected as much from my research.

I enter the following commands:

Sudo /bin/bash

Sudo mkdir /media/disk

Sudo mount -t ntfs-3g/dev/sda2/media/disk -o force

and I get this message:

>  root@ubuntu:~# sudo mount -t ntfs-3g/dev/sda2 /media/disk -o force
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
root@ubuntu:~# 


What am I doing wrong to get this message? 

Also on a side note, I'm using a LiveCD

---

### Post by taurus on 2008-12-18
There should be a space between ntfs-3g and /dev/sda2.

```

sudo mount -t ntfs-3g /dev/sda2 /media/disk -o force

```

---

### Post by Viveck on 2008-12-18
Yes that's it... Thank you.

I think I understand the command better now... I created the meda/disk dir and then you mount the /dev/sda2 to the [space] /media/disk and then force -o (all)

argh again thanks!

---

### Post by azzamite on 2008-12-18
> **Viveck said:**
> 
Sudo mount -t ntfs-[COLOR="DarkRed"]3g/de[/COLOR]v/sda2/media/disk -o force

and I get this message:
....
What am I doing wrong to get this message? 




mabe you missed a blankspace between ntfs-3g and /dev

---

