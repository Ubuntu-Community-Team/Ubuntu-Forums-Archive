---
title: "[SOLVED] problem installing kiba-dock plugins"
date: 2007-11-20
forum: Desktop Effects &amp; Customization
---

### Post by salmonella on 2007-11-20
hi,

I'm trying to install kiba-dock. I'm using instructions provided on the official website.
When I issue ./autogen.sh in the kiba-plugin folder I get

```

src/Makefile.am:132: Libtool library used but `LIBTOOL' is undefined
src/Makefile.am:132:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/Makefile.am:132:   to `configure.in' and run `aclocal' and `autoconf' again.
src/Makefile.am:132:   If `AC_PROG_LIBTOOL' is in `configure.in', make sure
src/Makefile.am:132:   its definition is in aclocal's search path.
src/Makefile.am: installing `./depcomp'
autoreconf: automake failed with exit status: 1

```

libtool package is already installed and AC_PROG_LIBTOOL is in configure.in under 'Checks for programs' section.

Could anyone please help?
thanks in advance

---

### Post by misamap on 2007-11-20
Go to this link for instructions:

[http://bearsolution.blogspot.com/2007/10/kiba-dock-osx.html](http://bearsolution.blogspot.com/2007/10/kiba-dock-osx.html)

---

### Post by salmonella on 2007-11-21
thanks a lot, misamap

---

