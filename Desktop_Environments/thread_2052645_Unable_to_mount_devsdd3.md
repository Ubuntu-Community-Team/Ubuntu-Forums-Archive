---
title: "Unable to mount /dev/sdd3"
date: 2012-09-03
forum: Desktop Environments
---

### Post by Ticklemehballlz on 2012-09-03
I have western digital caviar black as my main hard drive which holds Windows & Ubuntu on it. I also have a second one exactly the same in the SATA3 2 port and it was not mountable. So i put it into a external casing which is connected via USB3 and i get the same error only the device is changed from sbd2 to sdd3

Here is the Error i receive: > Error mounting: mount exited with exit code 12: NTFS signature is missing.
Failed to mount '/dev/sdd3': Invalid argument
The device '/dev/sdd3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


I am new to linux, This drive holds everything from thousands of movies, music, documents and games. I really need to access this hard drive to get 90% of my media. How can i get it to open on ubuntu? 

When i go to the Home folder, it is there twice "Backup/Media" but if i click either i get the Error shown above.


Thank you in advance to anyone that can help me!

Regards
kyle.

---

### Post by Bashing-om on 2012-09-03
kyle;   Hi ! welcome to the forum.

What you have is a disk formated as NTFS. This is a windows native environment that ubuntu can be made to cope with.
However, the error is indicative of file system faults. This being NTFS necessitates the use of windows tools !(Gparted = ubuntu) Will have to mount the drive to a windows machine and run the windows file system checkers on it.
 -Windows tools for Windows problems, linux tools for linux situations-

[INDENT]best of luck to you.
[/INDENT]

---

### Post by oldfred on 2012-09-03
If Linux is saying NTFS signature is missing, in Windows it may say RAW or unformated. That is the NTFS partition boot sector (PBR) is missing or not readable.

Sometimes testdisk can restore a damaged PBR from its backup.

As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

