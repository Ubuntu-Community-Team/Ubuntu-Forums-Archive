---
title: "Can't Execute Files Off External Drive"
date: 2009-01-03
forum: General Help
---

### Post by kidko on 2009-01-03
I've got most of my programing work on an external drive, /media/External. For some reason, any binary I end up with (generally a C++ program) cannot be run, due to the following error message:
```
-bash: ./program: Permission denied
```
(where ./program is the name of the program)
If I were to move program to, say, /home/kidko/program, it would run fine without any modifications. I can't figure it out!

I'm the owner of /media/External and External/*, and have rwx permissions on the same (and some drwx).

---

### Post by Polygon on 2009-01-03
i take it you have tried chmod +x on teh binaries you are trying to run on the external drive?

---

