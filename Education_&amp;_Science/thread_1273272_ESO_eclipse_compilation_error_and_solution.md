---
title: "ESO eclipse compilation error and solution"
date: 2009-09-23
forum: Education &amp; Science
---

### Post by mirandarson on 2009-09-23
Hi,
I recently had problems compiling ESO's eclipse software after updating to gcc-4.3. Because eclipse isn't supported since 2005, I had to find a solution on my own - which took a while, so I post it here in case someone's in the same situation once.

The error occurs while executing "make":

$make
...
In function ‘open’,
    inlined from ‘xmemory_malloc’ at src/xmemory.c:595:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
...

The solution is to modify the source code of the file mentioned in the error message. You have to change .../eclipse-5.0.0/qfits/src/xmemory.c:595 as follows:

ORIGINAL:    swapfd = open(fname, O_RDWR | O_CREAT);
NEW:             swapfd = open(fname, O_RDWR | O_CREAT, (S_IRUSR|S_IWUSR));

After that eclipse compiles, and I've been working with it for a few weeks without problems. However, I don't know exactly what I did, I simply followed the suggestions in [https://wiki.ubuntu.com/CompilerFlags#-D_FORTIFY_SOURCE=2](https://wiki.ubuntu.com/CompilerFlags#-D_FORTIFY_SOURCE=2)
There are some more suggestions in case this one doesn't work.
Hope that helps

Mirandarson

---

