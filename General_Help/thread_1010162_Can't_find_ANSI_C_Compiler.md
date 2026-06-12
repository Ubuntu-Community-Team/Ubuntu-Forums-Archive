---
title: "Can't find ANSI C Compiler"
date: 2008-12-13
forum: General Help
---

### Post by FXFman1209 on 2008-12-13
Hey everyone,

I'm trying to install something from source (a MOO server), and I'm getting the following error. Can anyone tell me why GCC isn't looking like it can compiler ANSI C stuff?? Thanks!

fxfitz@tvbox:~/moo/MOO-1.8.1$ sh configure
checking for bison
checking for byacc
checking for gcc
checking how to run the C preprocessor
checking whether -traditional is needed
checking how to run the C preprocessor
checking for NeXT
checking for the DEC Alpha running OSF/1
checking for the SGI compiler
checking for AIX
checking for POSIXized ISC
checking for minix/config.h
checking for -lintl
checking for A/UX
checking for HP/UX
checking that the C compiler handles important ANSI C constructs

*** Sorry, but I can't figure out how to find an ANSI C compiler here.
*** Compiling this program requires such a compiler.

---

### Post by nielz on 2008-12-13
Which version of ubuntu are you using and have you installed the gcc package?

(Try running gcc)

---

### Post by FXFman1209 on 2008-12-13
Hardy, and yes, GCC is installed and working.

fxfitz@tvbox:~$ gcc
gcc: no input files

---

### Post by |{urse on 2008-12-13
try g++ 

```
sudo apt-get install g++
``` 

it is ANSI compliant also.

---

### Post by FXFman1209 on 2008-12-13
Yup, that did the trick! I didn't even think of putting the C++ compiler in there. :-P

Thanks!

---

### Post by |{urse on 2008-12-13
Yeah i find it's best to have both gcc and g++ on your box ^^ Have a good one

---

### Post by mali2297 on 2008-12-13
Install the package **build-essential**. Then you will get the essential tools to compile from source: gcc, g++, make etc.

---

