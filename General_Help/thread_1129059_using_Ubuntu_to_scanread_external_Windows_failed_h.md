---
title: "using Ubuntu to scan/read external Windows failed hard drive"
date: 2009-04-18
forum: General Help
---

### Post by julie_r on 2009-04-18
I have Ubuntu 8 on my computer.

Windows XP (NTFS I believe) is on an external hard drive, and that drive FAILED a few years ago.

A year ago, a friend with a Windows computer was able to download freeware and look at files on my failed hard drive, so I know the failed external drive is capable of having files read from it.


I would like to be able to scan or copy files from that failed hard drive now, without having to use CDs or create images or any of that kind of complex stuff.

Is there any software/freeware for Ubuntu that would allow me to read and copy files from that external Windows hard drive?  I did install TestDisk, but I am not sure if that will do the job for me..

---

### Post by ddrichardson on 2009-04-18
[photorec]("http://www.cgsecurity.org/wiki/PhotoRec") is probably more what you're looking for.

---

### Post by julie_r on 2009-04-18
okay, I used PhotoRec/TestDisk... and this was the result:


Boot sector
Status: Bad

Backup boot sector
Status: Bad

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.



...... so, i guess that software won't work with this failed hard drive

---

### Post by danwood76 on 2009-04-18
you can normally make testdisk repair bad boot sectors.
Does it not give you the option?

---

