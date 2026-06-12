---
title: "make: gccmakedep: command not found"
date: 2006-08-02
forum: Desktop Environments
---

### Post by weeds86 on 2006-08-02
Hey guys,

Im new to linux and have installed it because I need to use it for uni. I am doing a programming course and am currently programming in c++. The uni wants us to use makefiles to link multiple classes. When I try run 'make' I get this error:

gccmakedep -- -Wall -pedantic-errors -g -- Student.cc studentDrv.cc Subject.cc
make: gccmakedep: Command not found
make: *** [depend] Error 127

I have installed the make package as well as gcc.

Does anyone have any suggestions on what to do to fix this problem

Cheers ;)

---

### Post by croak77 on 2006-08-02
Try with gcc -M instead of gccmakedep

---

### Post by weeds86 on 2006-08-02
I just tried gcc -M instead of gccmakedep and all it did was spit out approx 40 lines and then error:

make: *** No rule to make target '/usr/include/g++-3/iostream', needed bu 'Student.o'. Stop.

I have run this makefile on the linux machines at uni and it worked fine. There is nothing missing in the code.

Help is much appreciated.

Cheers ;)

---

### Post by weeds86 on 2006-08-02
If I replace the gccmakedep with makedepend it works. However I need it to have gccmakedep for the uni so how can I get gccmakedep on my home computer. Is there something to download and install?

Cheers ;)

---

### Post by weeds86 on 2006-08-03
nevermind quys... problem solved

---

