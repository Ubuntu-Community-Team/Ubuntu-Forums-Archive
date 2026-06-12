---
title: "XServ wont start , libfreetype.so.6"
date: 2008-11-22
forum: Desktop Environments
---

### Post by mastermind278 on 2008-11-22
My computer crashed while trying to install a program. When I started it up again, it did not load to X.

So I logged in and typed:
startx

It then returns:
/usr/bin/X11/X: error while loading shared libraries: libfreetype.so.6: cannot open shared object file: No such file or directory giving up.

xinit: No such file or directory (errno2): unable to connect to X server
xinit: No such process (errno3): Server error.

Can someone please help me with this error. I would prefer to repair this somehow rather than having to reinstall the whole OS. Thanks in advance.

---

### Post by mastermind278 on 2008-11-22
After doing some apt-get remove on a few files and an apt-get autoremove I was finally able to get X Server to start.

---

