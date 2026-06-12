---
title: "Emerald package not found in repo"
date: 2009-05-23
forum: Desktop Environments
---

### Post by nyxynyx on 2009-05-23
I just installed Ubuntu Jaunty but cant find the emerald package in repo. I enabled all the repo in Synaptic and reloaded the list but cant find emerald in it. Whats happening???

---

### Post by mk__ on 2009-05-23
I had the same problem - at Debian though..

If you've already installed the compiz package, then do the following:
Install the package (if you dont already have it) **git-core**
$ sudo aptitude install git-core
and then download the source from compiz' git repo:
$ git clone git://anongit.compiz.org/fusion/decorators/emerald
browse to the source directory
$ cd emerald/
start to configure it
$ ./autogen.sh
and then run
$ make
and then
$ sudo make

if you meet any errors, feel free to post them here.

---

### Post by nyxynyx on 2009-05-23
thanks! i tried downloading the items and when i try to run ./autogen.sh, i get the error "./autogen.sh: 9: autoreconf: not found"

How can i fix it?

---

### Post by mk__ on 2009-05-23
> **nyxynyx said:**
> thanks! i tried downloading the items and when i try to run ./autogen.sh, i get the error "./autogen.sh: 9: autoreconf: not found"

How can i fix it?

You need the autoconf package..

$ sudo aptitude install autoconf

---

### Post by nyxynyx on 2009-05-23
thanks i've downloaded the autoconf package. However, when i run ./autoconf.sh, i get 

Can't exec "libtoolize": No such file or directory at /usr/bin/autoreconf line 188.
Use of uninitialized value $libtoolize in pattern match (m//) at /usr/bin/autoreconf line 188.
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
configure.ac:16: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
autoreconf: configure.ac: tracing
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
engines/Makefile.am:37: Libtool library used but `LIBTOOL' is undefined
engines/Makefile.am:37:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
engines/Makefile.am:37:   to `configure.ac' and run `aclocal' and `autoconf' again.
engines/Makefile.am:37:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
engines/Makefile.am:37:   its definition is in aclocal's search path.
libengine/Makefile.am:8: Libtool library used but `LIBTOOL' is undefined
libengine/Makefile.am:8:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
libengine/Makefile.am:8:   to `configure.ac' and run `aclocal' and `autoconf' again.
libengine/Makefile.am:8:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
libengine/Makefile.am:8:   its definition is in aclocal's search path.
autoreconf: automake failed with exit status: 1


Sorry im not good at ubuntu.. just started.

---

### Post by trungchinh on 2009-06-17
Try

$ sudo aptitude install libtool

That solves the same problem for me

---

### Post by ~sHyLoCk~ on 2009-06-17
Do you have all the repos on, Multiverse? [Medibuntu]("https://help.ubuntu.com/community/Medibuntu")?

---

