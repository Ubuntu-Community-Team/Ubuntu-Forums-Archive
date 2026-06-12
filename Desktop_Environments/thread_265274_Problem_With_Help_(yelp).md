---
title: "Problem With Help (yelp)"
date: 2006-09-25
forum: Desktop Environments
---

### Post by fatsheep on 2006-09-25
My problem is that none of the help dialogs work, this includes the "About Ubuntu" and "System Documentation" links.  Here's the output of a command that may be useful in diagnosing this problem to some of you:

> fatsheep@fatsheep:~$ **yelp ghelp:about-ubuntu**
yelp: error while loading shared libraries: libgtkembedmoz.so: cannot open shared object file: No such file or directory


However, I've searched the repositories for the libgtkembedmoz.so package without any luck so I'm not sure what the problem could be.  :confused:

---

### Post by fatsheep on 2006-09-25
I've got the same problem with epiphany:

> fatsheep@fatsheep:~$ **epiphany**
epiphany: error while loading shared libraries: libgtkembedmoz.so: cannot open shared object file: No such file or directory


Perhaps this is a problem with gecko?  But if so then why does firefox work?

---

### Post by Greg Clark on 2007-02-19
I have the same problem with Yelp. It refuses to start. I have reloaded my breezy badger three times thinking it is something that went wrong during installation.. I have now tried starting yelp from shell and it gave the message:-  yelp: error while loading shared libraries: **libgtkembedmoz.so**: cannot open shared object file: No such file or directory.

Hope someone can help !

---

