---
title: "Can I get extra space for Ubuntu after I installed it with Wubi?"
date: 2009-02-01
forum: General Help
---

### Post by person9 on 2009-02-01
I installed Ubuntu using Wubi, and I thought 6 GB (maybe 8, dont remember) would be enough. But now that I installed all the programs I want, which were not very many, I have about 1.4 GB left. That's not enough for me.

Is there some simple way to let Wubi/Ubuntu use some more space than I initially told it during setup? 

I'm not interested in making a real partition or creating a whole new virtual disk for it to use.

---

### Post by person9 on 2009-02-01
This seems like a fairly straightforward question. . .

---

### Post by azmo35 on 2009-02-02
Hi,and yes look at [this]("http://ubuntuforums.org/showthread.php?t=438591") you will find the answer, samething called LVPM > 
Resizing virtual disks using LVPM

Run LVPM, and once the menu appears, select "resize" (to resize the root virtual disk, which contains both /home and the system files).

Input the new size, in MB, of the virtual disk.

Wait until the program finishes creating a new disks file and copying files from original home disk file; it will pop up a final instruction window instructing to backup the original home disk file and renaming the newly created disk file

Boot into windows and navigate to c:\wubi\disks, move the old virtual disk to a different folder as backup, and rename new.virtual.disk to root.virtual.disk

Reboot into ubuntu

If everything works, make sure you leave your vote on the poll, and if there's some error in the instructions or something didn't work, make sure leave a comment. i hope this help.

---

### Post by person9 on 2009-02-02
Thanks! So will using this LVPM pose any kind of a risk/threat to my computer's stability (i.e. Vista, or Ubuntu) or significantly affect the space on my hard drive?

Is it like creating a new virtual disk, copying everything over onto it, then deleting the old virtual disk? That seems like it'd take up a lot of space. I mean, yeah, no more than the 6GB I have now and whatever the new disk allotment is, but still..

It's just that I have heard some horror stories about a simple LVPM resize going wrong, and I'd like to make sure I know the risks before possibly damaging my perfectly running brand new laptop. :)

Also: It appears that LVPM will help me to make a *real* partition. Am I just misreading? I don't want a real partition, and I dont want a real Ubuntu install. I just wished to allow it to use up some more storage space as the virtual partition it already is.

---

### Post by ddeo on 2009-02-03
Hi, I am having low Free Space issues too but I wanted to make sure that I have to move my install to a new partition.

Firstly, I installed via Wubi

My HDD is 300GB.  When I view the Disk Usage Analyzer it says the following:

Total filesystem capacity: 286.5 (used 86.8 GB available: 199.7GB)

When I run sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa64688e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS



My problem is that if I open any directory at the bottom it says:
Free Space: 631.6 MB

If I delete any files this # does not change.

Please let me know if you think I need to follow the steps in the previous post or if I am missing something here...

Any help is appreciated.  Thanks, Dan

---

