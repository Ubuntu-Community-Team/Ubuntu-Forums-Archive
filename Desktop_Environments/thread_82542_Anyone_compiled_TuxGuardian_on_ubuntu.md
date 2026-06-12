---
title: "Anyone compiled TuxGuardian on ubuntu?"
date: 2005-10-26
forum: Desktop Environments
---

### Post by fannymites on 2005-10-26
I have been trying to compile TuxGuardian but it throws back so many errors and warnings it's not even funny.
examples - 
error: dereferencing pointer to incomplete type
warning: ‘struct xxxxType’ has virtual functions but non-virtual destructor
warning: incompatible implicit declaration of built-in function ‘exit

I've been googling for hours but I'm not getting anywhere.

---

### Post by jamesford on 2005-11-02
ive tried too and no luck. really wish someone can come up with a solution cos this looks like a very useful program, at least for me

---

### Post by az on 2005-11-02
It seems to want to make a kernel module, as well as the userspace binaries.  Are you using gcc-3.4?  Maybe it also needs cpp-3.4, too, since Ubuntu ships with gcc and cpp-4.0.

[http://tuxguardian.sourceforge.net/documentation.php](http://tuxguardian.sourceforge.net/documentation.php)

---

### Post by fannymites on 2005-11-02
I have gcc 3.4 and cpp 3.4 both installed but still no go, though I do still have 4.0 installed too so maybe it's a conflict or something?  I'm not prepared to make  
too many changes on ubuntu for the sake of one app.

I've also tried installing TuxGuardian on Fedora Core 4 and even recompiled the kernel but still got the same errors as on ubuntu.

---

