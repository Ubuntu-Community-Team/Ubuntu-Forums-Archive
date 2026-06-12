---
title: "problem at bootup in Breezy"
date: 2005-11-29
forum: Desktop Environments
---

### Post by Genesius on 2005-11-29
It was working fine this morning, but. . .

Boot up machine, I get to "mounting root filesystem" and get the following error:

cannot execute "etc/init.d/rcS"
Entering Runlevel : 2
cannot execute "etc/init.d/rc"

and then everything stops. 

My best guess is to run fsck, but I'm enough of a n00b that I'm not sure how to mount my Linux drive from the LiveCD. Linux is on hda1 (dual boot XP/Linux system with each OS on a separate HD).

Any ideas?

---

### Post by amohanty on 2005-11-30
mount -t ext3 /dev/hda1

if its an ext3 volume.

HTH
AM

---

### Post by Genesius on 2005-11-30
I'll give that a try. I think it's an ext2 volume, but I'll run **fdisk -l **first to make sure.

Do you think fsck will fix this, or is there something else I should try first?

---

### Post by Genesius on 2005-11-30
Well, I'm doing something wrong, but I don't know what. . .

I booted into the Live CD, opened Terminal, and ran **sudo fdisk -l** and got back

> Disk /dev/hda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           7        4982    39969720    7  HPFS/NTFS

Disk /dev/hdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         981     7879851   83  Linux
/dev/hdb2             982        1027      369495    5  Extended
/dev/hdb5             982        1027      369463+  82  Linux swap / Solaris



I then ran **mount -t ext2 /dev/hdb1** and got

> Usage: mount -V                 : print version
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
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .


So, what am I doing wrong? Is there any way for me to fsck hdb1 without mounting it first?

---

### Post by amohanty on 2005-11-30
I thinnk you can do this:
fsck -y /dev/hdb

HTH
AM

---

### Post by RAOF on 2005-11-30
[QUOTE=amohanty]mount -t ext3 /dev/hda1

if its an ext3 volume.

HTH
AM[/QUOTE]
Actually, you want
```
mount -t ext3 /dev/hda1 **/place/you/want/to/mount/it**
```
so, for example, having booted the livecd you could:
```
cd /mnt
mkdir ubuntu_root
mount -t ext3 /dev/hda1 ubuntu_root

```
to mount it to /mnt/ubuntu_root.

---

### Post by amohanty on 2005-11-30
whoops... my mistake. sorry about that.

AM

---

### Post by Genesius on 2005-12-01
[QUOTE=amohanty]I thinnk you can do this:
fsck -y /dev/hdb
[/QUOTE]

Tried it, and actually got fsck to respond. However, it responded with this:

> fsck 1.35 (28-Feb-2004)
e2fsck 1.35 (28-Feb-2004)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/hdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


](*,) 

So I tried ** e2fsck -b 8193 /dev/hdb** and got the same error.

](*,) ](*,) 

What I'm considering trying now is to burn a copy of the 5.10 Live CD, mount hdb using RAOF's instructions, and copying  /etc/init.d from the CD to the hard drive & see if that fixes the original error.

What do you think?

---

### Post by amohanty on 2005-12-01
Absolutely!!!
Thats the best part about having an active community, you get to try all of the above :) 

AM

---

### Post by RAOF on 2005-12-01
Actually, I think you should try
```
fsck -y /dev/hdb**1**
``` first.  That is, after all, the actual partition with your linux stuff on it (as shown by fdisk -l)

---

### Post by Genesius on 2005-12-01
That worked, found a bunch of errors. Unfortunately, it didn't fix the problem.

So next step, burn a copy of the 5.10 live CD and copy the /etc/init.d folder to my hard drive. If that doesn't work, copy /home to a CD & do a full reload.

---

