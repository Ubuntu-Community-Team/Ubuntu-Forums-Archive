---
title: "How do I install the Xlib sources for Ubuntu"
date: 2005-09-27
forum: Desktop Environments
---

### Post by bob k on 2005-09-27
I looked in snaptic and could only find the -dev and -dbg files. I'll most probably want a source meta package, if there is one.

Tia
Bob

---

### Post by lithorus on 2005-09-27
Try with "apt-src install packagename".

---

### Post by bob k on 2005-09-27
[QUOTE=lithorus]Try with "apt-src install packagename".[/QUOTE]

Well you got me on the right path. the command is apt-get source package name (xlib11-6 it will give you current base with a patch file), not a problem. I unpacked it in my home code directory using tar -xvf. I just wanted the code for reference. I guess if you wanted to compile from source the best place to put it would be /usr/src, any way I now know how to get source using apt-get.

Bob

---

