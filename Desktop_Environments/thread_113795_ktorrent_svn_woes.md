---
title: "ktorrent svn woes"
date: 2006-01-07
forum: Desktop Environments
---

### Post by stoeptegel on 2006-01-07
Hi there,

I love rufus, but i also want to keep track of the process of ktorrent. So i wanted myself to get the SVN version since it seems to have a lot of fixes, but this failed with:
(i followed the guide from the ktorrent site (faq))

```
$ make -f Makefile.cvs
This Makefile is only for the CVS repository
This will be deleted before making the distribution

./admin/cvs.sh: line 33: --version: command not found
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
make[1]: *** [cvs] Fout 1
make: *** [all] Fout 2
```

Autoconf 2.59a-3 is installed.

I have to say that i am new to CVS or SVN, so you might point me in the right direction.
Thanks for all help.

Edit
A bunch of headers fixed it:

* automake
* xlibs-dev
* kdelibs
* libqt3-headers
* libqt3-mt-dev
* kde-devel
(there might be some unneeded, but than sue my knowledge and not the messenger. )

---

### Post by GeneralZod on 2006-01-07
Can't be of much help, I'm afraid, except to say that it all works fine here :( I don't think I deviated from the instructions at all.

Have you tried doing

```

sudo apt-get build-dep ktorrent

```

?

I did this before trying and it prepared everything I needed for building.  Might be worth a try! :) The error is caused because the $AUTCONF variable is not being set, but I don't know enough about makefiles to diagnose why.

Edit: VVV

Doh - didn't see your edit! Anyway, glad you got it working!

---

### Post by stoeptegel on 2006-01-07
No i've got it working now, see my edit. Thanks though for the recommendation.

---

