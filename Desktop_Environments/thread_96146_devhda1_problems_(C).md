---
title: "dev/hda1 problems (C:)"
date: 2005-11-28
forum: Desktop Environments
---

### Post by syklitengutt on 2005-11-28
I have had some trouble with my grub
and fstab after makeing more space from D to Linux.

The grub problems are now fixed but im haveing some problems with my fstab 
and mounting dev/hda1 my windows c dir.
When mounting fstab I get this error:

> root@chris:~# sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

and here is the dmesg | tail
> root@chris:~# dmesg | tail
[4295587.173000] NTFS-fs error (device hda7): ntfs_ucstonls(): Unicode name co ntains characters that cannot be converted to character set cp437.
[4295675.297000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary  boot sector is invalid.
[4295675.298000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount o ption errors=recover not used. Aborting without trying to recover.
[4295675.298000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS v olume.
[4295695.183000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary  boot sector is invalid.
[4295695.183000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount o ption errors=recover not used. Aborting without trying to recover.
[4295695.183000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS v olume.
[4295727.189000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary  boot sector is invalid.
[4295727.189000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount o ption errors=recover not used. Aborting without trying to recover.
[4295727.189000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS v olume.


here is my fstab file:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults        0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda7       /media/hda7     ntfs    defaults        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


and here is my fdisk:
> root@chris:~# sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3696    29688088+   7  HPFS/NTFS
/dev/hda2            3697       14593    87530152+   5  Extended
/dev/hda5            3697        6307    20972822+  83  Linux
/dev/hda6            6308        6361      433723+  82  Linux swap / Solaris
/dev/hda7            6362       14593    66123508+   7  HPFS/NTFS
root@chris:~#



hope someone can help me.
Have some images i need in the windows directory, and I cant load windows anymore...
Dont really know why thougt.
dont get any error messages... it just jumps back to the grub os selector meny.

---

### Post by GeneralZod on 2005-11-28
That doesn't sound at all good to me :/ It's possible your C: was corrupted when you re-sized partitions.  Maybe try downloading Knoppix and seeing if you can access your Windows drives from there - it's set up to allow easy reading of NTFS drives.

---

### Post by syklitengutt on 2005-11-28
but ive been in windows after the resize.
But after I fixed grub and booted ubuntu again this problem started.
(it didnt happen before I edited grub to boot the right (hd0,4) for ubuntu)
before that I was able to use the starter to load windows.

Havnt done anything that could trash windows.

---

### Post by GeneralZod on 2005-11-28
[QUOTE=syklitengutt]but ive been in windows after the resize.
But after I fixed grub and booted ubuntu again this problem started.
(it didnt happen before I edited grub to boot the right (hd0,4) for ubuntu)
before that I was able to use the starter to load windows.

Havnt done anything that could trash windows.[/QUOTE]

Oh good - that's reassuring, at least :) I don't know how to solve your problem, I'm afraid, so I'll have to leave it to someone else.

---

### Post by syklitengutt on 2005-11-28
OK.... heres the facts.
Windows booted fine, linux didnt.
I changed grub settings, and made linux boot, but with a failure.
The failure was that it was unable to mount dev/hda1
if I take a look at dev/hda1 now its listed as ntfs unused space.

So if It somehow has been deleted shouldnt it be possible to
unformat it or get back what was on it?
nothing new has been written to it?

---

### Post by syklitengutt on 2005-11-28
bump

---

### Post by kosmic on 2005-11-28
If you restart your computer now, can you go to your Windows Partition (drive C:) in windows ? and list the contents ?

---

### Post by syklitengutt on 2005-11-29
ehhh... no....
If I try to load windows it just stops.
So my guess is that it has been formated.
But then again, it can only have been a quick format, so then it should be possible to get the most of the files back since it hasnt been written anything to the disk.

Any ideas of a linux prog that can do that?

---

### Post by dafl00 on 2005-11-29
MAYBE....
[http://www.cgsecurity.org/index.html?testdisk.html]("http://www.cgsecurity.org/index.html?testdisk.html")

dunno tho.. seems right.. good luck!!

---

### Post by kosmic on 2005-11-29
I think your drive is not formated, the NTFS partition become corrupted

---

### Post by syklitengutt on 2005-11-29
how to fix, or atleast get into it so I can get some of my files.
Ive booted it after reepartition.

---

### Post by remery on 2005-11-29
[QUOTE=syklitengutt]how to fix, or atleast get into it so I can get some of my files.
Ive booted it after reepartition.[/QUOTE]

I don't know for sure (still a newbie at this :-), but I had a similar problem. Booting into Windows and running chkdsk fixed it for me.

hth,
Rick

---

