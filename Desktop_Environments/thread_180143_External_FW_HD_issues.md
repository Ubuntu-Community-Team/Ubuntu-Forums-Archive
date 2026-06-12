---
title: "External FW HD issues"
date: 2006-05-21
forum: Desktop Environments
---

### Post by mc=2 on 2006-05-21
Irie you all!

For the past couple of hours I've been sifting the forums looking for some 
ideas/solutions to my issue.

Automount my 60gb external Lacie Drive. I use it to store my graphics created
under windows and as I'm trying to migrate, I'd like to be able to retrieve them
from Ubuntu as well.

What I did so far  - to no avail whatsoever  - is to add the following lines to /etc/fstab:

/dev/sda	/media/sda	vfat	defaults,user	0	0
/dev/sda1	/media/sda1	vfat	defaults,user	0	0

Results: no sda icons in /media neither on the Desktop.

Earlier on I did a dmesg just to realize that I understod f--- all (pardon my French) 
about it and I thought it was a good idea to attach it.

The only thing I can do is to hope in a kind spirit to help me through this!

Take care,

Marco

---

### Post by Ramses de Norre on 2006-05-21
Did you create the mountpoints?
```
sudo mkdir /media/sda1 && sudo mount -a
```
fstab nor mount does this automaticaly.

---

### Post by mc=2 on 2006-05-22
[QUOTE=Ramses de Norre]Did you create the mountpoints?
```
sudo mkdir /media/sda1 && sudo mount -a
```
fstab nor mount does this automaticaly.[/QUOTE]

Hi Ramses,
nope I din't. I've done it right now though:
#sudo mkdir /media/sda1
#sudo mkdir /media/sda

#sudo mount -a

Result is:

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

From what I can understand /dev/sda & /sda1 are not FAT partitioned...

I've just submitted the new demsg.txt and it seems something has
changed although I don't know what...

I suppose we're getting closer to the solution, thank you!!!

Let me know if you need some more info!

Have a good day,

Marco

---

### Post by mmcmonster on 2006-05-22
Interesting -

I have a firewire external HD partitioned as Fat32.  I *never* did any special configuration on my two Ubuntu machines (both running 5.10).

Both machines recognize the drive as soon as the drive is powered up.  The recognition happens over 95% or the time.  Maybe a couple times over the past 4-5 months it didn't get recognized, but it would work fine after a reboot.

---

### Post by Ramses de Norre on 2006-05-22
Could you post the output of sudo fdisk -l and the contents of fstab?

---

### Post by mc=2 on 2006-05-24
[QUOTE=Ramses de Norre]Could you post the output of sudo fdisk -l and the contents of fstab?[/QUOTE]

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1785    14337981    c  W95 FAT32 (LBA)
/dev/hda2            1786        8229    51761430    f  W95 Ext'd (LBA)
/dev/hda3            8230        9733    12080880   83  Linux
/dev/hda5            1786        8160    51207156    b  W95 FAT32
/dev/hda6            8161        8229      554211   82  Linux swap / Solaris

Disk /dev/sda: 61.4 GB, 61492838400 bytes
64 heads, 32 sectors/track, 58644 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       58644    60051440    b  W95 FAT32


*******

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda5       /media/hda5     vfat    defaults        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda	/media/sda	vfat	defaults,user	0	0
/dev/sda1	/media/sda1	vfat	defaults,user	0	0

The last two lines where added by me

Again thank you Ramses

---

### Post by mc=2 on 2006-05-24
[QUOTE=mmcmonster]Interesting -

I have a firewire external HD partitioned as Fat32.  I *never* did any special configuration on my two Ubuntu machines (both running 5.10).

Both machines recognize the drive as soon as the drive is powered up.  The recognition happens over 95% or the time.  Maybe a couple times over the past 4-5 months it didn't get recognized, but it would work fine after a reboot.[/QUOTE]

mmcmonster, thank you for your reply.
But did you ask yourself before posting:
"is this reply going to help somebody?"

8) Have a nice day anyhow!

Marco

---

