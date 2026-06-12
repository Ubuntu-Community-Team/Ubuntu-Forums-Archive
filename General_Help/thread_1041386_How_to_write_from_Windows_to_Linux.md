---
title: "How to write from Windows to Linux?"
date: 2009-01-16
forum: General Help
---

### Post by gm__ on 2009-01-16
Ive got one HDD with Ubuntu and another one with windows on NTFS.

How can i copy something from Windows to Linux?

---

### Post by taurus on 2009-01-16
If you want to access Ubuntu partition from windows, you need to use fs-driver.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by eagle416 on 2009-01-16
if you mount your windows partition in ubuntu, you can copy files across. That's what I do.

-EDIT- I meant windows DRIVE not partition, if that's what you have set up.

---

### Post by gm__ on 2009-01-16
Thanks for the help both of you!

Sorry looks like i didnt express myself clear enough.

Im running Ubuntu and i wanna copy from the windows drive.

Yes i mounted my windows drive because i can browse it and copy from linux to it but
not the other way.

---

### Post by halw on 2009-01-16
What I have done is to reduce your windows partition and create a new Fat32 partition. I use the fat32 partition to write files that I share between Ubuntu and Windows.

Just make sure the files you put on that partition are in a format that can be read/written by both, e.g., .doc, .xls and so forth.

---

