---
title: "Can I use ubuntu to repair XP on the same computer ?"
date: 2009-02-28
forum: General Help
---

### Post by horseradish on 2009-02-28
My windows xp seems to not load anymore. Is there a way I can recover it using ubuntu ? (which loads fine). Even if I could just get my music files.  

it doesn't seem to attempt to load, even in safe mode
can get the dos choices
windows recovery console : can't recall password (don't remember setting 
one.)
safemode, it seems to stop at pavsysboot. i don't have panda antivirus, but 
did use the online scan a few times.
boot with last good settings : nothing
i don't recall anything that would corrupt it

---

### Post by taurus on 2009-02-28
I am not sure if you can fix your windows from Ubuntu.  However, you can still access that ntfs partition to backup your files though.  You just need to mount it before you can access it.

Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That would be a lower case letter L, not number 1.

---

### Post by horseradish on 2009-02-28
Thanks. I will try that.

---

### Post by horseradish on 2009-02-28
it says ( minus the disk identifier)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         653     5245191   1b  Hidden W95 FAT32
/dev/sda2   *         654        9728    72894937+   7  HPFS/NTFS

---

### Post by taurus on 2009-02-28
You can try to mount those two partitions while in Ubuntu.  From a terminal, run

```
sudo mkdir /media/sda1 /media/sda2
sudo mount -t vfat /dev/sda1 /media/sda2 -o umask=000
sudo mount -t ntfs-3g /dev/sda2 /media/sda2
df -h
```
If there is an error message, especially mounting /dev/sda2, post the whole message here.

---

### Post by horseradish on 2009-02-28
I think that first file may be returnil program, which i installed but never used. it made a new section on the disk

I got this back:

:~$ sudo mkdir /media/sda1 /media/sda2
mkdir: cannot create directory `/media/sda1': File exists
mkdir: cannot create directory `/media/sda2': File exists
x@ubuntu:~$ sudo mount -t vfat /dev/sda1 /media/sda2 -o umask=000
x@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda2 /media/sda2
x@ubuntu:~$ df -h

---

### Post by horseradish on 2009-03-04
> **horseradish said:**
> My windows xp seems to not load anymore. Is there a way I can recover it using ubuntu ? (which loads fine). Even if I could just get my music files.  

it doesn't seem to attempt to load, even in safe mode
can get the dos choices
windows recovery console : can't recall password (don't remember setting 
one.)
safemode, it seems to stop at pavsysboot. i don't have panda antivirus, but 
did use the online scan a few times.
boot with last good settings : nothing
i don't recall anything that would corrupt it

someone posted the following on the xp forums. is this worth a go to recover my xp ? and if so how do i do this with ubuntu ?

[B]Here's an inexpensive trick that sometimes fixes this. Power down, and
attach the drive to another running system, or, reboot with a Linux boot
disk or anything else that recognises NTFS and doesn't lock the drive.

From the root of the drive, delete the hidden/system file "pagefile.sys".
You may also want to delete "hiberfil.sys". Empty the wastebasket, put the
drive back in its place, and reboot. The first boot may be slow and you
may have to power off, then on again.

I've used this a number of times to successfully restart systems that behave
the way you describe. [/B]

---

