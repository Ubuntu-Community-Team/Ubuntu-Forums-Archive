---
title: "When i delete files with shred it leaves behind the file"
date: 2006-07-14
forum: Desktop Environments
---

### Post by Andrew12106 on 2006-07-14
is it meant to do this or should it delete the file from view

---

### Post by K.Mandla on 2006-07-14
I think it's supposed to. Every time I've used it, it has left behind the file, and I just went ahead and deleted it.

I know it's working though, because I've double-checked the "shredded" files, and they were garbled.

---

### Post by Andrew12106 on 2006-07-14
good, i was afraid it wasnt working.

---

### Post by AZzKikR on 2006-07-14
I believe the man page for shred says:
> overwrite a file to hide its contents, and optionally delete it
When I shred a file I issue the command:
```
shred -fuz [file]
```
The flag -u truncates and removes the file after overwriting.

---

