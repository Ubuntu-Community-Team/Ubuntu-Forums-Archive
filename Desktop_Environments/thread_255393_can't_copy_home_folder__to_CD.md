---
title: "can't copy home folder  to CD"
date: 2006-09-11
forum: Desktop Environments
---

### Post by seatea on 2006-09-11
I want to copy my home folder so I can have the information for later when I do a fresh install of Dapper. I tried with gnomebaker and could not write the information. The  write failed due to a permission denied error. I then tried with K3b, which seems to give better informatio, and again could not write due to error. I am having problems with my system after upgrading to Dapper, the data in some files seems to be corrupted, so I am planning a clean install. I ran fsck which gave me a clean bill of help, but all is not well. Here is the output from K3b:

"System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-26-powerpc
Devices
-----------------------
HITACHI DVD-ROM GD-7000 016J (/dev/hdc, ) at /media/cdrom0 [CD-ROM; DVD-ROM] [Error] [None]

SONY CD-RW  CRX160E 1.0e (/dev/scd0, ) at  [CD-R; CD-RW; CD-ROM] [Error] [SAO; TAO; RAW; SAO/R96R; RAW/R96R]
K3b
-----------------------
Size of filesystem calculated: 0

mkisofs
-----------------------
/usr/bin/X11/mkisofs: No such file or directory. Invalid node - seatea/Desktop/Keep Nautilus from misbehaving
/usr/bin/X11/mkisofs: No such file or directory. Invalid node - seatea/Desktop/Keep Nautilus from misbehaving".

I tried removing the file "Keep Nautilus from  Misbehaving", but it did no good  because I got another error message for a different file after that.

What can I do to get my home folder copied to a CD?

---

### Post by BerkeleyDude on 2006-09-11
"Invalid node" sounds pretty bad.

For the next file that causes this problem, could you run "stat *file*", and post the output here?

---

### Post by seatea on 2006-09-11
Thanks for taking the time to look at my problem. I removed the "Keep Nautilus from Misbehaving" file, tried to burn again and got this error message:
"mkisofs
-----------------------
/usr/bin/X11/mkisofs: No such file or directory. Invalid node - Documents/Linux Stuff/Linux Tips/Managing an OS emergency
/usr/bin/X11/mkisofs: No such file or directory. Invalid node - Documents/Linux Stuff/Linux Tips/Managing an OS emergency".

I ran stat on "Managing an OS emergency" amd got this output:
"stat: cannot stat `Managing an OS emergency': No such file or directory".

---

### Post by seatea on 2006-09-14
I never figured out  the problem with the files, but I did manage to burn an ISO of my home  folder. It seems there were only two problem files. I moved  them out  of  my home folder and burned the ISO.

---

