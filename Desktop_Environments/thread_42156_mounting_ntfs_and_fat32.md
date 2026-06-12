---
title: "mounting ntfs and fat32"
date: 2005-06-16
forum: Desktop Environments
---

### Post by themoddingden on 2005-06-16
Hi;
I've tried the guide version of mounting my ntfs drive and couldn't get it to work.
heres the deal i see all the drives in media but they will not mount this is done by default .
I want to be able to read the other drives i have mp3's text etc on them that i'd like to use in linux.
I run kubuntu is there something different I need to do ???
heck even the new knoppix will not let me view them it's rather slow and doesn't know about my fx5700 reports it as unknown .
I even tried the mount -a but no luck what do i need to do to get it to work???

---

### Post by desdinova on 2005-06-16
[QUOTE=themoddingden]Hi;
I've tried the guide version of mounting my ntfs drive and couldn't get it to work.
heres the deal i see all the drives in media but they will not mount this is done by default .
I want to be able to read the other drives i have mp3's text etc on them that i'd like to use in linux.
I run kubuntu is there something different I need to do ???
heck even the new knoppix will not let me view them it's rather slow and doesn't know about my fx5700 reports it as unknown .
I even tried the mount -a but no luck what do i need to do to get it to work???[/QUOTE]

What errors do you get? To help fix it, people need to know what went wrong

---

### Post by themoddingden on 2005-06-16
hi;
said it windows/hda1 was already in there or the like in the konsole.
and like i said i see the drives but they can't be mounted.
i click on the drive and it says error can't mount .
i right click and it tells me unmounted drive .
i even edited etc/fstab:
 with dev /hda1 ntfs umask=00222 0 0 
in it like the one guide said to do but that doesn't work either.
I see all drives on a default install but they are not mounted/mountable.

---

### Post by desdinova on 2005-06-16
Is that your line from /etc/fstab? If so, you haven't specified where it is to be mounted.

Post your /etc/fstab

---

### Post by Iuliux on 2005-06-16
look at my fstab -  I have fat & ntfs partitions:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               reiserfs notail          0       1
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /mnt/c          ntfs    umask=002       0       0
/dev/hda5       /mnt/d          vfat    umask=000       0       0
/dev/hda6       /mnt/e          vfat    umask=000       0       0

---

### Post by Takis on 2005-06-16
Try
```
 # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda7 / reiserfs notail 0 1
/dev/hda8 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hda1 /mnt/c ntfs [COLOR=Blue]defaults,[/COLOR]umask=002 0 0
/dev/hda5 /mnt/d vfat [COLOR=Blue]defaults,[/COLOR]umask=000 0 0
/dev/hda6 /mnt/e vfat [COLOR=Blue]defaults,[/COLOR]umask=000 0 0
```
Out of curiousity, why are you using reiserfs?

---

### Post by themoddingden on 2005-06-22
hi;
found it stupid humasn error/ late night editing it helps to use the freaking right dev lol
But thank you all

---

### Post by brandonyoung on 2005-06-22
Takis,

Is there a reason not to use reiserfs?  I'm still very new to linux, but I thought Reiserfs had a good general performance for a file system from general reviews that I've seen.

--Brandon Young

---

### Post by tristian on 2005-06-22
I was skimming through the comments and I might have missed things.

(words in red are commands)
Here is how to check what partions and drives you have:
[COLOR=Red]/sbin/fstab -l[/COLOR] - this will list all devices
Here is an example of my output:
Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2294    18426523+  83  Linux
/dev/hdc2            2295        2424     1044225   82  Linux swap

Disk /dev/hdd: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4906    39407413+   7  HPFS/NTFS
/dev/hdd2            4907        7475    20635492+   f  W95 Ext'd (LBA)
/dev/hdd5            4907        6374    11791678+   7  HPFS/NTFS
/dev/hdd6            6375        7475     8843751    b  W95 FAT32

Next you will want to open up fstab:
[COLOR=Red]nano /etc/fstab[/COLOR]
(note: this file is set up into sections. The columns are divided by pressing <tab> do not use spaces)

You can add to this file like on my fdisk output /dev/hdd5 would be added to this file like this:
/dev/hdd5  <tab>  /place/to/mount/it  <tab>  ntfs  <tab>  defaults  <tab>  0 0


Note: FAT paritions get mounted under vfat

---

### Post by Takis on 2005-06-22
[QUOTE=brandonyoung]Takis,

Is there a reason not to use reiserfs?  I'm still very new to linux, but I thought Reiserfs had a good general performance for a file system from general reviews that I've seen.

--Brandon Young[/QUOTE]
Well, as long as you realise your distro will normally use ext3, and you're aware that (however unlikely) it is possible that using a different file system may break things or cause things not to work, there's not a problem. I'm thinking maybe a program or two exists that requires a feature of ext3 that reiser doesn't have, in which case things get complicated. The reverse probably won't happen because most Ubuntu users have ext3 not reiser.

IMHO, performance differences would be negligible unless you're doing constant disk I/O. Naturally it's up to each person, but I would say unless you have a specific reason for reiser, just use ext3.

---

