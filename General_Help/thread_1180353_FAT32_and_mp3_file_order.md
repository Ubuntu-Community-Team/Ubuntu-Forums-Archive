---
title: "FAT32 and mp3 file order"
date: 2009-06-06
forum: General Help
---

### Post by kelargo on 2009-06-06
Someone gave me a USB flash drive with a bunch of mp3s. 
The mp3s are an audio book and the files are named in an appropriate order.
When I plug the USB flash drive into my car radio receiver, the files are played back out of order. I think the files are out of order from when they were originally copied onto the USB flash drive. I think the person used XP.

I am looking for a utility to reorder the files in the FAT32 partition on the USB flash drive.  I remember reading about such a utility in Windows XP.
Does anyone know of such a way to manipulate the files on FAT32 to be in the appropriate order?

tia!

---

### Post by t4ggs on 2009-06-06
try renaming them with 1 2 3...

---

### Post by kelargo on 2009-06-06
I can try renaming them.. the files are currently names things like this:

> 
Chapter 01 - The...mp3
Chapter 02 - Sp...mp3


so the files have the appropriate named order. 
I think the problem has to do with the en bloc copy that occurred when the folder was copied over and how the files ended up on the partition.

---

### Post by kelargo on 2009-06-06
ok, renaming the files, individually, to the following, corrected the playback order problem..

> 
01_Chapter 01 - The...mp3
02_Chapter 02 - Sp...mp3 


how to do this with a single bash command line?

thanks

---

### Post by t4ggs on 2009-06-07
dont know, im still a nob hehe

---

### Post by thundre on 2010-08-31
I'm having the same problem.  I make a FAT32 USB stick with multiple folders, and the files in the folders are in semi-alphabetical order (as seen by my car stereo) when I want them in exact-alphabetical order.  

Maybe there's a mount option that will fix this?

---

### Post by gibzaki on 2011-03-03
You have to re order the allocation table.
Check out this site.
[http://www.murraymoffatt.com/software-problem-0010.html](http://www.murraymoffatt.com/software-problem-0010.html)

There are many tools to re-order the files alphabetically.
In Ubuntu you can install fatsort.
Then sudo apt-get install fatsort

Copy your mp3 in folders with the proper names...

To sort your pendrive run something like this (umount the device first):
sudo fatsort -c -oa /dev/sdb1

You can check the files sorting using fatsort -l /dev/sdb1

:)

---

### Post by kelargo on 2011-03-11
That's an interesting utility! thanks!

---

