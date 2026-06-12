---
title: "cd copy + read only"
date: 2006-02-25
forum: Desktop Environments
---

### Post by GQed76 on 2006-02-25
I just copied a large amount of data off a CD and all the files are read only.  Is there a way to make all of them writable without having to click into each folder and selecting all, preferences, permissions?

---

### Post by dcstar on 2006-02-25
[QUOTE=GQed76]I just copied a large amount of data off a CD and all the files are read only.  Is there a way to make all of them writable without having to click into each folder and selecting all, preferences, permissions?[/QUOTE]
In a terminal, try:

chmod +w -R *

---

### Post by taurus on 2006-02-25
The reason they are all read only because that's what the permission on the CD!  So, you just have to "chmod" them by hand then (from terminal)...

```

chmod 644 *

```

---

### Post by GQed76 on 2006-02-26
thanks..was just supprised the gui didnt allow for subfolders as well

---

### Post by cdsboy on 2006-02-26
just do chmod -R 777 *path to folder* saves alot of time

---

### Post by GQed76 on 2006-05-07
Interesting...when i did chmod 644 *, all the files became unknown and ??? and 0 kb and i cant access them

---

### Post by GQed76 on 2006-05-07
777 worked tho :)

---

