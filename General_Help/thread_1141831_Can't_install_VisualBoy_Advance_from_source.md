---
title: "Can't install VisualBoy Advance from source"
date: 2009-04-28
forum: General Help
---

### Post by Envergure on 2009-04-28
Of all the things I've tried to install from source, the only one that worked was LMMS.  I don't honestly know how difficult it is to package source files for distribution properly, but I might assume people get it wrong most of the time if I were unaware of my own neophytery.

I entered the directory, using the terminal, and typed "./configure".  When that finished I typed "make", which stopped with error messages after about 2 seconds.  While it was running it gave off all sorts of messages, ending with "error:  cast from char* to u32 loses precision".

I am using VBA version 1.72.  [[EDIT:  Tried 1.71 and the same thing happened.]]

In the meantime I'll try an older version.

If I can just get binaries somewhere that would be great (already tried [www.getdeb.net](www.getdeb.net)) but I really should learn how to install stuff from source.

---

### Post by Envergure on 2009-04-28
I just thought of this while I was doing the dishes, can someone tell me if it's right please?

A conversion from char* (pointer to a char) to u32 (unsigned 32-bit integer) would be valid on a 32-bit system with 32-bit pointers, but since my system is 64-bit it doesn't work as a 64-bit pointer gets either truncated (the "loss of precision") or has its most-significant 32 bits lopped off, which is just as bad.

Since the last update to VBA was in 2004, when 64-bit hardware wasn't so common as now, it may never have occurred to the developers to make the code compatible with both 32- and 64-bit compilers.

Is that right?

If it is right, how can I get around it?




[[EDIT]]
I had a look at the code.  There's a lot of it.  It's mostly C with a bit of x86-assembly, and loads of numbers in hexadecimal.  Some of the files are virtually devoid of comments.  There's no way I'm going to try to edit it!

---

### Post by Envergure on 2009-04-29
OK, I found some binaries.

---

