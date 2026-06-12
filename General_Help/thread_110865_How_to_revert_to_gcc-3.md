---
title: "How to revert to gcc-3"
date: 2005-12-31
forum: General Help
---

### Post by AngelSL on 2005-12-31
I can't seem to revert to gcc 3, apt only has the base. Is there any other way i can get it??

---

### Post by professor_chaos on 2005-12-31
find gcc-3 as a .deb file on the internet and install it with "sudo dpkg -i gcc-3" or whatever.

---

### Post by jdong on 2005-12-31
What do you mean by that? If you want to install older versions of GCC by packages like gcc-3.4, gcc-3.3, etc in main and universe.

However, if you want to make the whole system use GCC 3 instead of 4, that's going to be a very difficult and messy recompiling job.


Why do you need to do so anyway?

---

### Post by AngelSL on 2006-01-05
I need to because i need to compile UnrealIRCD. It doesnt work with gcc 4

---

### Post by hw-tph on 2006-01-06
The gcc-3.4 (or gcc-3.3) metapackage in the Ubuntu repositories will most likely work fine. Install it and then invoke the configure script with **CC=/usr/bin/gcc-3.4 ./configure** and make it with **CC=/usr/bin/gcc-3.4 make**.


Håkan

---

