---
title: "Drives Formatted"
date: 2008-12-11
forum: General Help
---

### Post by Julius1988 on 2008-12-11
I accidentally executed rm -r command inside the /media directory, now i have lost all the files how to retrieve it? the removal was quick  i don't think 300gigs would have gone in a second.

---

### Post by bryncoles on 2008-12-11
check out photorec and testdisc (they're the same program, and available in the repos).

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

theres a nice walkthrough on how to use them on that website. you'll need a drive as big as the one you're recovering from though, in order to have somewhere to put any recovered files. 

good luck!

---

### Post by hyper_ch on 2008-12-11
restore the files from your backups.

---

### Post by blazemore on 2008-12-11
Yeah just copy the files from your most recent backups... I don't understand what the problem is.

Seriously though, unplug your pc don't bother shutting down. Boot off the LiveCD and use Testdisk to try and recover your files. I wouldn't get too hopeful though.

---

### Post by Julius1988 on 2008-12-11
Photorec_static is working it is able to recover files.Is there a way to restore the entire directory structure.

---

### Post by bryncoles on 2008-12-11
dunno about directory structure, sorry! at least the files are coming back though. maybe someone else can chip in with directory structure information...?

---

### Post by Julius1988 on 2008-12-11
Could some one help to do the same in linux using shell or whatever suitable.

link:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec]("http://www.cgsecurity.org/wiki/After_Using_PhotoRec")

---

### Post by Julius1988 on 2008-12-11
> **Julius1988 said:**
> Could some one help to do the same in linux using shell or whatever suitable.

link:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec]("http://www.cgsecurity.org/wiki/After_Using_PhotoRec")

sorry i failed to notice the script was in python.
I dont know how to execute python script,could i get some help here.

---

### Post by Sef on 2008-12-11
>  		Photorec_static is working it is able to recover files.Is there a way to restore the entire directory structure. 	

Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").  From the site:

> **TestDisk** is a *powerful* free data recovery software! It was primarily designed to help **recover lost partitions** and/or **make non-booting disks bootable again** *when* these symptoms are caused by *faulty software*, certain types of *viruses* or *human error* (such as *accidentally* deleting a Partition Table). Partition table recovery using TestDisk is really easy. 

---

### Post by asker on 2008-12-11
If you have Python, just run python "name of file" in the command line.

---

### Post by Julius1988 on 2008-12-11
I was able to recover the FAT32 using testdisk but what about NTFS and EXT3?I am not able to undelete.

---

