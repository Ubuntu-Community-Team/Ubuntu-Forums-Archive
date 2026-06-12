---
title: "LinuxCommand"
date: 2009-02-24
forum: General Help
---

### Post by Lekshmi on 2009-02-24
In UNIX , whole disk space is divided into slices.

we can get the size of a slice by using the command 
devstat -FI slicename

this will give the information like how much is the size, how much used, how much is free...

just like this, how we will know about the size of storage device in LINUX?
My disk is a SCSI disk. Which command will help me??

---

### Post by stumbleUpon on 2009-02-24
```
df -h
```

will show the way in which the disk has been paritioned and also the size of each partition.

```
du -hs filename/foldename
```

will display the size of the given file or folder.

Consult the man pages for more information on each command.

---

