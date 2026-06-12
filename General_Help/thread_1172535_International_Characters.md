---
title: "International Characters"
date: 2009-05-28
forum: General Help
---

### Post by midna on 2009-05-28
I have a cifs mount that has multiple folders with many different international characters in it. I do not have gui access and  the international characters are not being displayed correctly. For instance, Gymnope?dies should be Gymnope&#769;dies and H?stk?nslor should be Höstkänslor. The mount is in /etc/fstab:

```
//172.31.7.117/mount /media/raid/Audio/mounted cifs username=remote,password=<hidden>     0       0
```

I have tried 
```
//172.31.7.117/mount /media/raid/Audio/mounted cifs username=remote,password=<hidden>,iocharset=utf8     0       0
```

and
```
//172.31.7.117/mount /media/raid/Audio/mounted cifs username=remote,password=<hidden>,iocharset=utf8,codepage=cp850     0       0
```

and 

```
//172.31.7.117/mount /media/raid/Audio/mounted cifs username=remote,password=<hidden>,iocharset=utf8,codepage=437     0       0
```

Where 437 comes from running "chcp" on the windows machine.

I'm at a loss in making the international characters display correctly so that I can use the files and folders seamlessly between the Ubuntu and windows machine.

---

### Post by midna on 2009-05-29
bump :(

---

