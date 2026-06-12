---
title: "Please help, Make command won't work!"
date: 2006-09-21
forum: Desktop Environments
---

### Post by dontpanic0 on 2006-09-21
Hi, in the install information file it says:
> You need a recent kernel, at least 2.6.6 or 2.4.26, with header files
for the kernel. Make sure there is a link to the kernel source from
the modules directory. The command

  ls /lib/modules/`uname -r`/build

should have at least 'include' directory and '.config' file.

When I do that command it says that there is no such file or directory.  How do I fix this?

---

### Post by NetworkGuy on 2006-09-21
You need to install the make program.
From a terminal type:

```
sudo apt-get install make 
```

---

### Post by dontpanic0 on 2006-09-21
Thanks!  I have a new problem now so im editing my first post.

---

