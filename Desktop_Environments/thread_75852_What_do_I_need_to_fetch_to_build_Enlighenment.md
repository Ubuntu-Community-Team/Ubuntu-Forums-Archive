---
title: "What do I need to fetch to build Enlighenment???"
date: 2005-10-14
forum: Desktop Environments
---

### Post by piggyaugu on 2005-10-14
I got the enlightenment 17 CVS. 

But I cannot build it. 

I've done "apt-get install build-essential"

and I added automake manually

it still gave me this when I run the autogen.sh

```

augu@blackbox:~/.e17install/e17/apps/e$ ./autogen.sh
Running aclocal...
aclocal:configure.in:18: warning: macro `AM_ENABLE_SHARED' not found in library
aclocal:configure.in:19: warning: macro `AM_PROG_LIBTOOL' not found in library
aclocal:configure.in:172: warning: macro `AM_GNU_GETTEXT' not found in library
aclocal:configure.in:173: warning: macro `AM_GNU_GETTEXT_VERSION' not found in library
Running autoheader...
Running autoconf...
configure.in:18: error: possibly undefined macro: AM_ENABLE_SHARED
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:19: error: possibly undefined macro: AM_PROG_LIBTOOL
configure.in:172: error: possibly undefined macro: AM_GNU_GETTEXT
configure.in:173: error: possibly undefined macro: AM_GNU_GETTEXT_VERSION
augu@blackbox:~/.e17install/e17/apps/e$


```


What else do I need to build such a wm?

---

### Post by Ampersand on 2005-10-14
Most of the dependancies can be found here:
[http://www.get-e.org/User_Guide/English/_pages/2.1.html](http://www.get-e.org/User_Guide/English/_pages/2.1.html)
Makew sure you have the -dev packages for each of these. If there's anything else missing, the configure script will tell you about it.

---

