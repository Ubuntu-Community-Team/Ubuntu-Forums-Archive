---
title: "Read only..."
date: 2005-11-09
forum: Desktop Environments
---

### Post by Donnut on 2005-11-09
Is there anyway to give all the subfolders and files in a file write permission?  I am currently going through all the files and folders I copied from NTFS drives read-write permission.

---

### Post by paddyg on 2005-11-09
in termnial
```
chmod -R 755 dir
```
(755 or whatever you like)

if you want to see what's happening:
```
chmod -R -v 755 dir
```

for chmod options:
```
chmod --help
```

---

### Post by frodon on 2005-11-09
I think a "chmod -R +w" of the source directory will do the job.

---

