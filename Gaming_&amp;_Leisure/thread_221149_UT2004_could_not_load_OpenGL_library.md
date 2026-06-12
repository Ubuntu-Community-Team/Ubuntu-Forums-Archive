---
title: "UT2004 could not load OpenGL library"
date: 2006-07-22
forum: Gaming &amp; Leisure
---

### Post by ironfistchamp on 2006-07-22
This is a fresh install of Dapper and I have just put the latest nvidia (non-free) drivers on. When starting UT2004 I get

***@ubuntu:~$ ut2004
Could not load OpenGL library

History:

Exiting due to error


Can anyone help? Thanks

Ironfistchamp

---

### Post by vem0m on 2006-07-22
and u are sure that u have 3d Acceleration? type into terminal "glxinfo" and post the output of that here

---

### Post by ironfistchamp on 2006-07-22
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


not a clue what that is all about. UT2004 used to work perfectly before I trashed the system. I have a 7800GTX if the info helps.

Thanks

---

### Post by professor_chaos on 2006-07-22
your missing nvidia-glx

```
sudo apt-get install nvidia-glx
```

---

