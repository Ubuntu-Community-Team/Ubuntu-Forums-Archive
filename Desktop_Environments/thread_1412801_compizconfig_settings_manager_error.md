---
title: "compizconfig settings manager error"
date: 2010-02-21
forum: Desktop Environments
---

### Post by cyberey66 on 2010-02-21
I recently installed 9.10 AMD64 and now I cant seem to use the compizconfig settings manager.

I previously had 9.10 i386 installed and it worked perfectly.  When I try and launch the settings manager I get this error:

:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 99, in <module>
    import compizconfig
ImportError: /usr/lib/python2.6/dist-packages/compizconfig.so: invalid ELF header

Any suggestions?  I can't configure compiz which prevents me from properly setting up my desktop.  Are there any other ways to configure compiz?

---

### Post by cyberey66 on 2010-02-28
Purged everything with the name compiz in it, reinstalled compiz, now it works.

---

