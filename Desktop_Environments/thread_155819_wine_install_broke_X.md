---
title: "wine install broke X"
date: 2006-04-05
forum: Desktop Environments
---

### Post by pataphysician on 2006-04-05
edit: bimberi in #ubuntu helped me out with this.

*sudo apt-get install -reinstall libsm6*

solved the problem.
---------------------------
i tried to install wine using the howto in this thread:

[http://ubuntuforums.org/showthread.php?p=894484](http://ubuntuforums.org/showthread.php?p=894484)

when i got to the point where you're supposed to run wine for the first time, i received an error message:

err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory

and then i slowly started noticing that applications weren't responding quite right. applications wouldn't launch, nautilus wouldn't open. so i restarted. now X won't start. when i do *startx* i get the error:

xauth: error while loading shared libraries: libXau.so.6: cannot open shared object file: No such file or directory.

in /usr/X11R86/lib i have the following:

lrwxrwxrwx 1 root root 11 2006-04-05 16:33 libXau.so -> libXau.so.6
lrwxrwxrwx 1 root root 13 2005-10-02 20:11 libXau.so.6 -> libXau.so.6.2
-rw-r--r-- 1 root root 7.7k 2005-08-31 00:42 libXau.so.6.2

also, when i was compiling wine, i got an error that said i had to get rid of /usr/X11R6/lib/libGL.a, so i renamed it. i've since renamed it back.

please help!

---

