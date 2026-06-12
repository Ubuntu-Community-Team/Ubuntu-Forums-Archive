---
title: "External HDD stopped mounting automatically"
date: 2009-02-15
forum: General Help
---

### Post by SneakPeak on 2009-02-15
Hi,

I am running 8.10 Ubuntu.  I have a Seagate Free Agent USB external HDD. On previous versions of Ubuntu I had some trouble mounting it but under 8.10 I had no problems from installation.  It was mounting automatically at every boot and then I tried to get Samba to start automatically at every boot and somehow I have caused the external HDD to stop mounting automatically.  I now have to mount the drive manually at every boot using:

sudo mount /dev/hdc /home/fatbob/exthdd/

How can I go back to getting it to auto mount.  It has only an NTFS partition on it and when I do mount it with the above command it uses fuseblk.

Any help would be great.

Thanks

Sneaks

---

### Post by SneakPeak on 2009-04-21
Bump!

I would really appreciate some help on this!

Thanks

Sneaks

---

### Post by SneakPeak on 2009-04-21
I have tried unplugging and re-plugging the drive to see if it would mount.  I get the following error:

"Cannot mount volume"
"Details"
"mount_point cannot contain the following characters: new line, G_DIR_SEPARATOR (Usually /)"

I don't know where it is getting the mount point from because I have removed all reference to this drive / partition in the fstab.

The drive label used to be "FreeAgent Drive" and I thought the space in the drive label may be causing the problem.  I therefore used ntfstools to change the lable to "ExternalHDD"  This didn't help, I still got the same error.

I can mount the drive manually using:

mount /dev/sdc1 /home/adrian/exthdd

but plugging and unplugging doesn't give an automatic mount.  I figure if I can get the automatic mount working I have a chance of getting the mount at boot working?

Sneaks

---

### Post by SneakPeak on 2009-04-23
Ok so my disk was less than half full so with the help of gparted I managed to:

First shrink the ntfs partition
Second create and ext3 partition
Third move all data from ntfs partition to ext3 partition
Forth delete ntfs partion
Fifth grow ext3 partition to fill disk

Now when I boot the drive mounts automatically at /media/ExtHDD

Question is how do I get it to mount to a different location?

As soon as I put an entry into /etc/fstab that specifies a different location the disk doesn't mount at all.  I have tried /dev/sdc2 and the UUID of the drive in /etc/fstab but no luck

Any, any help?

Thanks

Sneaks

---

### Post by SneakPeak on 2009-04-23
Ok so in desperation and since there are no willing helpers out there I have created a symbolic link between /media/ExtHDD and the folder I really want to mount the drive on!  It is not perfect but it may work for my needs.  I want to now share some stuff using Samba I hope a symbolic link can be shared!

Sneaks

---

