---
title: "SWonder 2"
date: 2006-03-24
forum: Desktop Environments
---

### Post by gummer on 2006-03-24
Hi,

I'm quite new to linux / ubuntu, but i need it for my WFS(wave field synthesis) project. Wonder is a program created for WSF.

I install the program without much troubles but when I try to open it, it gives me the following error:

swonder: error while loading shared libraries: libswonder.so.1: cannot open shared object file: No such file or directory

Strange, the file "libswonder.so.1" is shared and located at /usr/local/lib, but still he doesn't find it.

What to do? 

Grtz,

gummer

---

### Post by tedius on 2006-03-24
As you say it looks like it can't find the library.  The first thing that I would check is to make sure that /usr/local/lib is in you LD_LIBRARY_PATH.

To do this open up a terminal and type;
```
echo $LD_LIBRARY_PATH
```
This will print out all the location where it will check for libraries.

I you can't find /usr/local/lib her you will have to add it your self, so type;
```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib
```

To make it a permanent fix you will have to add it to your .profile file in you home directory.

---

### Post by gummer on 2006-03-24
that worked great, thx man :)

---

