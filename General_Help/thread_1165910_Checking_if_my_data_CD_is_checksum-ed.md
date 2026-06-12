---
title: "Checking if my data CD is checksum-ed"
date: 2009-05-21
forum: General Help
---

### Post by BuntuFirstTimer on 2009-05-21
I wonder if I can check my data CDs to find whether they are checksum-ed during the burning process.

Is checksum a necessary process for burning a data CD?

---

### Post by Bindsa on 2009-05-21
To check whether the data is burned correctly you can use this:
```
md5sum [file]
```
Where [file] is the designated filename (make sure you are using the command from the directory where the file is located). Write that number down, burn the data to the cd and check again. If they match their checksums are right.

---

