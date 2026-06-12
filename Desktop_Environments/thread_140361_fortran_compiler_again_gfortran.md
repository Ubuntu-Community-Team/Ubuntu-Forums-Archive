---
title: "fortran compiler again: gfortran"
date: 2006-03-06
forum: Desktop Environments
---

### Post by GAW-Snow on 2006-03-06
I installed the new ubuntu version and went ahead and installed all the compilers I needed.  There seems to be something wrong this time.

When I tried to compile a source using gfortran it would tell me all the bugs.  After all the bugs are fixed, I got the following message.

> /usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status


I tried gcc and the same message came up.

These are all source codes that I know for sure would work.  They worked before I switched to the new version.

I'm guessing there is something I'm missing in the base system, probably a bug.  I'm a physicist, not a computer programmer, so any help would be appreciated.

---

### Post by Ampersand on 2006-03-06
have you tried getting the build-essential package from apt? It might have something that you missed.

---

### Post by zugvogel on 2006-03-06
[QUOTE=Ampersand]have you tried getting the build-essential package from apt? It might have something that you missed.[/QUOTE]

I have to agree with this suggestion: I had the same problem a while ago and doing this fixed it for me.

---

### Post by GAW-Snow on 2006-03-08
So, what package do I need to install?  Is it "build-essential"?  Because there isn't one listed in synaptic.

---

### Post by GAW-Snow on 2006-03-08
Nevermind, I found the package.  Installing it right now.  Thanks.

---

