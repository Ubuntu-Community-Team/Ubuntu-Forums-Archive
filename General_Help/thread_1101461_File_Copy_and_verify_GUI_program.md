---
title: "File Copy and verify GUI program"
date: 2009-03-20
forum: General Help
---

### Post by kehon on 2009-03-20
i need a program for linux/ubuntu 8.10 that will allow me to drag and drop or copy past files from my laptop hard drive to and external desktop hard drive and verify they were copied correctly so that i can make sure it is right because i'm going to wipe the hard drive and reinstall everything and i want to be sure that all the files were correctly copied i can also do md5 but i cant find a GUI application that will verify alot of files and save so when i copy i can have it verify once more any suggestions

---

### Post by Wayne_V on 2009-03-20
mkdir <destination>
cd <source>
find . | cpio -pdm <destination>
diff -rq <source> <destination>

make sure <destination> is not under <source>

---

### Post by kehon on 2009-03-20
i want a gui application cause there are going to be alot of copying talking about thousands of files and command line just wont work when i'm trying to organize the files while i'm at it cause i cant type in paths to well also dont like cmd

---

### Post by oldos2er on 2009-03-20
grsync

---

### Post by kehon on 2009-03-20
anything with drag and drop so i can add files to another directory cause i'm trying to organize as i move and thanks for this i will use it in the mean time

---

