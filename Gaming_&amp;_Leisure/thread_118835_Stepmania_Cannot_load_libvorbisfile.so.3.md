---
title: "Stepmania: Cannot load libvorbisfile.so.3"
date: 2006-01-17
forum: Gaming &amp; Leisure
---

### Post by slinga on 2006-01-17
Hey all, 

Can someone help me get Stepmania to work? I downloaded the binary and I get the following error message: 

> ./stepmania
./stepmania: error while loading shared libraries: libvorbisfile.so.3: cannot open shared object file: No such file or directory


As you can see I have the file installed in /usr/lib:
> 
ls -l /usr/lib | grep libvorbis
-rw-r--r--   1 root root   237654 2005-07-21 20:16 libvorbis.a
-rw-r--r--   1 root root  2093074 2005-07-21 20:16 libvorbisenc.a
-rw-r--r--   1 root root      889 2005-07-21 20:16 libvorbisenc.la
lrwxrwxrwx   1 root root       21 2006-01-12 22:21 libvorbisenc.so -> libvorbisenc.so.2.0.0
lrwxrwxrwx   1 root root       21 2006-01-12 17:46 libvorbisenc.so.2 -> libvorbisenc.so.2.0.0
-rw-r--r--   1 root root  1939456 2005-07-21 20:16 libvorbisenc.so.2.0.0
-rw-r--r--   1 root root    32348 2005-07-21 20:16 libvorbisfile.a
-rw-r--r--   1 root root      896 2005-07-21 20:16 libvorbisfile.la
lrwxrwxrwx   1 root root       22 2006-01-12 22:21 libvorbisfile.so -> libvorbisfile.so.3.1.0
lrwxrwxrwx   1 root root       22 2006-01-16 18:18 libvorbisfile.so.3 -> libvorbisfile.so.3.1.0
-rw-r--r--   1 root root    28320 2005-07-21 20:16 libvorbisfile.so.3.1.0
-rw-r--r--   1 root root      846 2005-07-21 20:16 libvorbis.la
lrwxrwxrwx   1 root root       18 2006-01-12 22:21 libvorbis.so -> libvorbis.so.0.3.0
lrwxrwxrwx   1 root root       18 2006-01-12 17:46 libvorbis.so.0 -> libvorbis.so.0.3.0
-rw-r--r--   1 root root   171848 2005-07-21 20:16 libvorbis.so.0.3.0





an ldd on the binary gives this: 
> ldd stepmania
        linux-gate.so.1 =>  (0xffffe000)
        libvorbisfile.so.3 => not found
        libvorbis.so.0 => not found
        libogg.so.0 => not found
        libmad.so.0 => not found
        libSDL-1.2.so.0 => not found
        libpthread.so.0 => /lib32/tls/libpthread.so.0 (0x55584000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x55596000)
        libXtst.so.6 => /usr/lib32/libXtst.so.6 (0x55656000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0x5565b000)
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0x556fa000)
        libdl.so.2 => /lib32/tls/libdl.so.2 (0x55770000)
        libpng12.so.0 => /usr/lib32/libpng12.so.0 (0x55773000)
        libz.so.1 => /usr/lib32/libz.so.1 (0x55798000)
        libjpeg.so.62 => /usr/lib32/libjpeg.so.62 (0x557ac000)
        libstdc++.so.5 => /usr/lib32/libstdc++.so.5 (0x557cb000)
        libm.so.6 => /lib32/tls/libm.so.6 (0x55885000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0x558a7000)
        libc.so.6 => /lib32/tls/libc.so.6 (0x558b2000)
        /lib/ld-linux.so.2 (0x55555000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x559e1000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0x559e4000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0x559e8000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0x559f5000)
> > > > > > > 

---

### Post by slinga on 2006-01-17
Forgot to mention I'm on AMD64. I hope someone has some ideas, if not I guess I'm going to have to dual boot with SuSE 10.0. Stepmania worked perfect there. Thanks in advance, I appreciate it.

---

### Post by Perfect Storm on 2006-01-18
Have you tried making a symblink?

---

### Post by slinga on 2006-01-18
Can you give me more details. The file /usr/lib/libvorbisfile.so.3 is in fact a symlink. I created another symlink in /usr/lib32 but it still would not work.

---

### Post by Perfect Storm on 2006-01-18
Is it a dynamic or static installation you made?

Edit: Sorry, I didn't look closely enough, dynamic I see.

---

### Post by slinga on 2006-01-19
Ok let's try a different route. I can't compile Stepmania (CVS) from source either: 

> ./autogen.sh
configure.ac:150: warning: AC_LIB_PREPARE_PREFIX is m4_require'd but is not m4_defun'd
configure.ac:150: AC_LIB_PREPARE_PREFIX is required by...
autoconf/m4/iconv.m4:20: AM_ICONV_LINKFLAGS_BODY is expanded from...
configure.ac:150: AM_ICONV_LINKFLAGS_BODY is required by...
autoconf/m4/iconv.m4:75: AM_ICONV_LINK is expanded from...
autoconf/m4/iconv.m4:103: AM_ICONV is expanded from...
configure.ac:150: the top level
configure.ac:150: warning: AC_LIB_RPATH is m4_require'd but is not m4_defun'd
configure.ac:150: AC_LIB_RPATH is required by...
configure.ac:150: warning: AC_LIB_PREPARE_PREFIX is m4_require'd but is not m4_defun'd
configure.ac:150: AC_LIB_PREPARE_PREFIX is required by...
autoconf/m4/iconv.m4:20: AM_ICONV_LINKFLAGS_BODY is expanded from...
configure.ac:150: AM_ICONV_LINKFLAGS_BODY is required by...
autoconf/m4/iconv.m4:75: AM_ICONV_LINK is expanded from...
autoconf/m4/iconv.m4:103: AM_ICONV is expanded from...
configure.ac:150: the top level
configure.ac:150: warning: AC_LIB_RPATH is m4_require'd but is not m4_defun'd
configure.ac:150: AC_LIB_RPATH is required by...
configure.ac:150: warning: AC_LIB_PREPARE_PREFIX is m4_require'd but is not m4_defun'd
configure.ac:150: AC_LIB_PREPARE_PREFIX is required by...
autoconf/m4/iconv.m4:20: AM_ICONV_LINKFLAGS_BODY is expanded from...
configure.ac:150: AM_ICONV_LINKFLAGS_BODY is required by...
autoconf/m4/iconv.m4:75: AM_ICONV_LINK is expanded from...
autoconf/m4/iconv.m4:103: AM_ICONV is expanded from...
configure.ac:150: the top level
configure.ac:150: warning: AC_LIB_RPATH is m4_require'd but is not m4_defun'd
configure.ac:150: AC_LIB_RPATH is required by...
configure.ac:150: warning: AC_LIB_PREPARE_PREFIX is m4_require'd but is not m4_defun'd
configure.ac:150: AC_LIB_PREPARE_PREFIX is required by...
autoconf/m4/iconv.m4:20: AM_ICONV_LINKFLAGS_BODY is expanded from...
configure.ac:150: AM_ICONV_LINKFLAGS_BODY is required by...
autoconf/m4/iconv.m4:75: AM_ICONV_LINK is expanded from...
autoconf/m4/iconv.m4:103: AM_ICONV is expanded from...
configure.ac:150: the top level
configure.ac:150: warning: AC_LIB_RPATH is m4_require'd but is not m4_defun'd
configure.ac:150: AC_LIB_RPATH is required by...


Any idea what this is about?

---

### Post by BlahMan_of.Doom on 2007-06-29
I don't mean to revive a realy really really realy old thread, but I'm kind of having the same problem in Feisty. :\

---

### Post by Cappy on 2007-07-21
> **BlahMan_of.Doom said:**
> I don't mean to revive a realy really really realy old thread, but I'm kind of having the same problem in Feisty. :\

Sorry I didn't see this until now. Getlibs works really well with stepmania:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by kimbrasil on 2008-09-05
I'm bumping the topic, but is because recently I had the same problem.
to fix it i was installed libvorbisfile3
and I also have problem with libsdl 1.2

$ sudo apt-get install libsdl1.2debian libvorbisfile3

---

