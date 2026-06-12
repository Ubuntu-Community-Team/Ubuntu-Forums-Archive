---
title: "Premature plugout caused filesystem corruption: missing folders&amp;files from USB drive"
date: 2009-02-14
forum: General Help
---

### Post by canakas on 2009-02-14
Dear all,

Some of you have most likely been in the situation where a USB drive has been prematurely plugged out from an external device, or from windows boxes.

This time an 8GB Corsair Flash Voyager (FAT32) was prematurely plugged out from an HP All-in-one scanner, while there were file operations going on.
The HP scanner seems not only to read or index the USB drive, but also write to it. Why do I think so? Well, the label(name) of the USB drive, which I had set to "Name", now appears when mounted in Ubuntu(hardy) as NAME; in all capitals.

Now to add to my frustration, half of my files and folders where missing :(

First of all I made a dd image of the disk, so now I can start down the road towards recovering my files and folders ---

How do I so this? I ran a few checks and copied the backed up bootsector over the new bootsector with TESTDISK, which made no difference. Nor can TESTDISK see the files and folders that are missing. I have run PHOTOREC onto another, disk but just as a way of getting my hands on the files I need for work.

Is there any way of getting the foldertree restored? The files are really less important than the folders.

I appreciate very much your help.

best regards
canakas

---

### Post by cariboo on 2009-02-14
I would suggest using [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to restore your missing files. Testdisk is in the repositories, you can use Add/Remove Programs, Sysnaptic Package Manager and of course the command line to install it.

Jim

---

### Post by cdtech on 2009-02-14
If this is an NTFS journal you could Run 'ntfsfix' on Ubuntu which will reset the NTFS journal. You would first need to install the ntfsprogs:
```
sudo apt-get install ntfsprogs
then do a ntfsfix /dev/?
```
This is if the device was unplugged. If the filesystem is corrupt you could try the program testdisk which is used to scan and repair disk partitions. You'll need to install it using:
```
sudo apt-get install testdisk
```
Just maybe a direction you could take to try and repair........

---

### Post by canakas on 2009-02-14
Thanks for your replies people.

As I stated Testdisk doesn't do what I need, and I think we can agree that Photorec leaves a bit of a mess, even though they are excellent last resorts :)

Is there no other way to rebuild the foldertree?

---

### Post by canakas on 2009-02-15
I have now looked through the files from the Photorec restauration and many files are there, but I would like to see the folders...

Well, I tried foremost and got a cleaner result, with all the files in folders name by their extension. This helps a little bit at least. Still no folders though. 

I will try CnWRecovery's software which has a search for directory stubs and post back with the results.

-canakas

---

