---
title: "Error while extracting .rar archive"
date: 2006-01-20
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-01-20
I tried to extract two different .rar archives from two diffeent sources today, and recieved the same error:

When right-clicking the archive, and choosing "Extract here", two EMPTY folders with identical names (except for the last character) are created.

When opening the archives with File Roller 2.12.1, I can see all the files (each archive ontains one folder, that contains all files), but when double clicking on one of the files, an error message is displayed: ```
An error occurred while extracting files. Cannot create /tmp/fr-C01Oo5/Folder Name/File Name
```

How come?

Thanx

G

---

### Post by art on 2006-01-20
In terminal type
 unrar e filename.rar
That should extract the file. If you don't have unrar
 sudo apt-get install unrar

---

