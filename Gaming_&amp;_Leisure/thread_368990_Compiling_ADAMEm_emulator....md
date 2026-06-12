---
title: "Compiling ADAMEm emulator..."
date: 2007-02-24
forum: Gaming &amp; Leisure
---

### Post by bebop_tango on 2007-02-24
I'm having hardships compiling [adamem]("http://www.komkon.org/~dekogel/adamem.html") on Ubuntu...

You can compile using either linux/SVGALib or Unix/X drivers, or both.

Here's what I got by trying to compile the Unix/X version:

```
make -f Makefile.X
make[1]: Entering directory `/home/lmello/emulador/adamem.tar.gz_FILES'
gcc      -Wall -O2 -fomit-frame-pointer -DLSB_FIRST -DUNIX_X -DUNIX -DMITSHM -DHAVE_CLOCK -DSOUND -DZLIB   -c -o Coleco.o Coleco.c
Coleco.c:620: error: conflicting types for &#8216;Z80_Out&#8217;
Z80IO.h:33: error: previous declaration of &#8216;Z80_Out&#8217; was here
Coleco.c:767: error: conflicting types for &#8216;Z80_In&#8217;
Z80IO.h:28: error: previous declaration of &#8216;Z80_In&#8217; was here
Coleco.c: In function &#8216;GetSnapshotParams&#8217;:
Coleco.c:1128: warning: pointer targets in passing argument 1 of &#8216;strlen&#8217; differ in signedness
Coleco.c:1128: warning: pointer targets in passing argument 1 of &#8216;__builtin_strcmp&#8217; differ in signedness
Coleco.c:1128: warning: pointer targets in passing argument 1 of &#8216;strlen&#8217; differ in signedness
Coleco.c:1128: warning: pointer targets in passing argument 1 of &#8216;__builtin_strcmp&#8217; differ in signedness
Coleco.c:1128: warning: pointer targets in passing argument 1 of &#8216;__builtin_strcmp&#8217; differ in signedness
Coleco.c:1128: warning: pointer targets in passing argument 1 of &#8216;__builtin_strcmp&#8217; differ in signedness
Coleco.c: In function &#8216;_SaveSnapshotFile&#8217;:
Coleco.c:1254: warning: pointer targets in passing argument 1 of &#8216;strcpy&#8217; differ in signedness
Coleco.c:1259: warning: pointer targets in passing argument 1 of &#8216;strcpy&#8217; differ in signedness
Coleco.c:1265: warning: pointer targets in passing argument 1 of &#8216;strcpy&#8217; differ in signedness
Coleco.c: In function &#8216;StartColeco&#8217;:
Coleco.c:1496: warning: suggest explicit braces to avoid ambiguous &#8216;else&#8217;
make[1]: *** [Coleco.o] Error 1
make[1]: Leaving directory `/home/lmello/emulador/adamem.tar.gz_FILES'
make: *** [x] Error 2


```

I could overcome these errors by commenting the declarations of the functions Z80_Out and Z80_In in the Z80IO.h file, and declaring them in Coleco.c instead.

When I tried again, similar errors occured with all PutPixel* functions in X.c - again, I managed to avoid this annoying error with similar procedure.

But then another error came in the makefile... the script tries to invoke "(...) make -makefile (..)" somewhere but the make program cannot be issued with the "-makefile" option!

](*,) 

Has anybody successfully compiled this emulator under Ubuntu...?

---

### Post by bebop_tango on 2007-02-24
I'm having some issues... I was able to compile but even then it didn't work...

This is my personal log as a text file (I'm unable to properly format the text here...)

---

### Post by bebop_tango on 2007-07-30
I did it!

I think the code is so old that the compiler the author used some compiler that didn't care much about *matching* declarations... there were a few issues in Coleco.c/IO

There's a problem in the makefiles - it does compile an executable named makedata and it needs to be executed before going through. The problem is you'll probably compile this NOT in any of your $PATH directories, so I corrected the call from "makedata" to "./makedata".

I'll post the updated tarball soon.

---

