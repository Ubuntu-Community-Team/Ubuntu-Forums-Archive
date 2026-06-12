---
title: "compiling ndiswrapper"
date: 2006-09-10
forum: Desktop Environments
---

### Post by jcrnan on 2006-09-10
Im trying heavily to compile ndiswrapper but I cant seem to get the whole link to kernel thing.

this is what says in the install file:

Prerequisites 
=============

You need a recent kernel, at least 2.6.6 or 2.4.26, with header files
for the kernel. Make sure there is a link to the kernel source from
the modules directory. The command

  ls /lib/modules/`uname -r`/build

should have at least 'include' directory and '.config' file.

Now how do I do this? Ive tried putting the kernel source inside the directory it talks about but that doesnt help.. Please someone tell me step by step how to fix this?

---

