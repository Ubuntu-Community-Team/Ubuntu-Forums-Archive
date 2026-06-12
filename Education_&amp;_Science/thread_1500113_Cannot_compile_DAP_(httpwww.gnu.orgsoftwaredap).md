---
title: "Cannot compile DAP (http://www.gnu.org/software/dap)"
date: 2010-06-02
forum: Education &amp; Science
---

### Post by drpereira on 2010-06-02
I am trying to compile dap (project for statistics, free alternative to sas) ([http://www.gnu.org/software/dap);](http://www.gnu.org/software/dap);) but get the following error when trying to "sudo make":
```

daniel@daniel-laptop:~/Desktop/dap-3.7$ sudo make
Making all in src
make[1]: Entering directory `/home/daniel/Desktop/dap-3.7/src'
gcc -DPACKAGE_NAME=\"GNU\ dap\" -DPACKAGE_TARNAME=\"dap\" -DPACKAGE_VERSION=\"3.7\" -DPACKAGE_STRING=\"GNU\ dap\ 3.7\" -DPACKAGE_BUGREPORT=\"bug-dap@gnu.org\" -DPACKAGE=\"dap\" -DVERSION=\"3.7\" -DSTDC_HEADERS=1 -DHAVE_SYS_WAIT_H=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_FCNTL_H=1 -DHAVE_STRINGS_H=1 -DHAVE_UNISTD_H=1 -DHAVE_MKDIR=1 -I.     -g -O2 -MT dap0.o -MD -MP -MF .deps/dap0.Tpo -c -o dap0.o dap0.c
dap0.c:546: error: conflicting types for ‘getline’
/usr/include/stdio.h:651: note: previous declaration of ‘getline’ was here
make[1]: *** [dap0.o] Error 1
make[1]: Leaving directory `/home/daniel/Desktop/dap-3.7/src'
make: *** [all-recursive] Error 1

```

What I am doing wrong :confused:

---

### Post by drpereira on 2010-06-11
bump  

):P

---

### Post by spinoza666 on 2010-06-13
In your output it says:
```
dap0.c:546: error: conflicting types for ‘getline’
/usr/include/stdio.h:651: note: previous declaration of ‘getline’ was here

```

I don't know what this means, but getline is included in the manpages-dev package, so may be worth a shot installing it. If not I would see if I could find out if there were more packages which provide this command than one, and perhaps purging the superfluous ones.

---

### Post by spinoza666 on 2010-06-13
Hey,

it seems there's a bug which corresponds with your error:

[http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg187011.html]("http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg187011.html")

so my earlier suggestion will probably not work.

---

