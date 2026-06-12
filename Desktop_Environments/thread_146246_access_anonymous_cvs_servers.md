---
title: "access anonymous cvs servers?"
date: 2006-03-17
forum: Desktop Environments
---

### Post by kasemodz on 2006-03-17
I'm trying to get the new drivers for my rtl8185 card and I have to access this cvs.
cvs.sourceforge.net:/cvsroot/rtl8180-sa2400 

How do I access these servers or any cvs server in general?

---

### Post by claes on 2006-03-18
To login to the cvs server
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/rtl8180-sa2400 login

To download:
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/rtl8180-sa2400 co ***modulename***

Claes

---

