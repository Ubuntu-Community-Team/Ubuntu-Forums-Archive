---
title: "cairo-dock error"
date: 2009-02-15
forum: General Help
---

### Post by Pro$pect on 2009-02-15
when trying to run cairo-dock I get the following error:

cairo-dock: error while loading shared libraries: libdbus-glib-1.so.2: cannot open shared object file: No such file or directory

Can I not use cairo with 64bit ubuntu? I installed the latest version of 2.0 and the plug-ins.

---

### Post by AlexBellisBrown on 2009-02-15
Have you ever run Cairodock before on your machine?

---

### Post by fabounet on 2009-02-16
to install a 32bits package on a 64bits machine, use **getlibs**
it works well.

---

### Post by RavanH on 2009-02-17
- OR - 

Define the official cairo-dock repo which contains a **working** 64bit version. See instructions on [http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en#8-32 bits AND 64 bits]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en#8-32 bits AND 64 bits")

:)

---

### Post by Pro$pect on 2009-02-17
> **RavanH said:**
> - OR - 

Define the official cairo-dock repo which contains a **working** 64bit version. See instructions on [http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en#8-32 bits AND 64 bits]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en#8-32 bits AND 64 bits")

:)

That's how I installed cairo and this is the error I'm getting:

cairo-dock: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory

---

### Post by zeltak on 2009-02-22
hi

Getting the same error for a normal 32 bit install...so maybe it doesnt have to do with 64 bit

Zeltak

---

### Post by ovizii on 2009-02-22
tried every possible trick, followed those links, doesn't help :-(

any other advice?

---

### Post by fabounet on 2009-02-22
did you try to install libgtkglext ?

---

### Post by ovizii on 2009-02-23
> root@titan:/# apt-cache search libgtkglext
libgtkglext1 - OpenGL Extension to GTK+ (shared libraries)
libgtkglext1-dbg - OpenGL Extension to GTK+ (debugging symbols)
libgtkglext1-dev - OpenGL Extension to GTK+ (development files)
libgtkglext1-doc - OpenGL Extension to GTK+ (documentation)
libgtkglext1-ruby - GTK+ GL extension bindings for the Ruby language
libgtkglext1-ruby1.8 - GTK+ GL extension bindings for the Ruby language
libgtkglextmm-x11-1.2 - C++ wrapper for the OpenGL Extension to GTK (shared libraries)
libgtkglextmm-x11-dev - C++ wrapper for the OpenGL Extension to GTK (development files)
root@titan:/#

i installed all these in the hope it would help but the error remains :-(

---

