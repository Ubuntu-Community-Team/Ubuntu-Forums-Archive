---
title: "whatprovides libiberty.so"
date: 2009-02-10
forum: General Help
---

### Post by kramulous on 2009-02-10
Hi,

  Does anybody know where libiberty.so (or the source to build) exists?  My usual search methods are coming up empty.

  There is some info on the sunfreeware site ([http://www.sunfreeware.com/libiberty.html](http://www.sunfreeware.com/libiberty.html)) but it doesn't quite 'smell' right given what I want it for.

  I'm trying to compile the latest version of an open source profiler: [http://oprofile.sourceforge.net/download/](http://oprofile.sourceforge.net/download/)

Ubuntu 8.10 x86_64

Cheers,
me

---

### Post by sdennie on 2009-02-10
I'm not sure but, if you are trying to build a version of something that is already in the repos, this will get all the stuff you probably need:

```

sudo apt-get build-dep oprofile

```

---

### Post by geraldm on 2009-02-10
binutils package
It is also created by the gcc compiler suite.

---

### Post by unutbu on 2009-02-10
```
apt-file search libiberty
```yields```

binutils-dev: /usr/include/libiberty.h
binutils-dev: /usr/lib/libiberty.a
binutils-dev: /usr/lib/libiberty_pic.a
gcc-snapshot: /usr/lib/gcc-snapshot/lib/libiberty.a
gcc-snapshot: /usr/lib/gcc-snapshot/lib64/libiberty.a
ghdl: /usr/lib/ghdl/lib/libiberty.a
llvm-gcc-4.2: /usr/lib/llvm/gcc-4.2/lib/libiberty.a
mingw32: /usr/i586-mingw32msvc/lib/libiberty.a

```
Maybe you are looking for either binutils-dev or gcc-snapshot?

---

### Post by kramulous on 2009-02-10
Thank you.  

I was hesitate to install from the repos due to needing it on another machine with no Internet connection.

The apt-file solution is the one I award the gold star.  It'll help me with a lot of other things.  Thanks unutbu.

Also a big thanks to sdennie and geraldm

---

