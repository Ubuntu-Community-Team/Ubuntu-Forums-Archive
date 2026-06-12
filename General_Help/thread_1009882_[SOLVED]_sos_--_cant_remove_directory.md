---
title: "[SOLVED] sos -- cant remove directory"
date: 2008-12-13
forum: General Help
---

### Post by lordbux on 2008-12-13
pls help me
when i tryed to remove a file that i put in my home directory 
it says  " read only file system" :confused:
and wont let me delet
i tryed everuything... changing permissions (wont change-same mesage), changing ownership (wont change-same)

how can i delete this directory :popcorn:

pls help

---

### Post by Elfy on 2008-12-13
You could use nautilus with root rights ```
gksudo nautilus
``` or do it from the cli with sudo

```
sudo rm -r ~/path/to/directory
```

---

### Post by Arup on 2008-12-13
Removing to trash with sudo will make that file end up in root trash so make sure to empty root trash as well.

---

### Post by Iowan on 2008-12-13
A read-only filesystem frequently means something got corrupted.  Probably not the case if all else is working properly.

---

### Post by lordbux on 2008-12-14
thanks guys 
all of u
woooh solved it.... 
anyway
advanced happy Christmas and new year greetings :KS
long live opensource:popcorn:
u guys rock:guitar:

---

