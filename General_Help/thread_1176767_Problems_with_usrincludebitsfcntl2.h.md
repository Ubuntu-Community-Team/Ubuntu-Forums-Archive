---
title: "Problems with /usr/include/bits/fcntl2.h"
date: 2009-06-02
forum: General Help
---

### Post by MichaelBarnes on 2009-06-02
I am attempting to install a package from source.  The configure runs fine.  When I run make, I get the following error:

/usr/include/bits/fcntl2.h:51: error: call to '__open_missing_mode'
declared with attribute error: open with O_CREAT in second argument
needs 3 arguments

I am running Ubuntu 9.04.  In searching the web, I find many references to this error appearing in the installation of various packages.  The problem is, this exact error shows up in bug reports for a bunch of packages, and patches are developed for those packages.  

I am very new to Ubuntu and I am not a programmer at all.  However, logic indicates to me that if a whole bunch of packages have a problem with fcntl2.h, I find it hard to believe that all those package developers independently made the same mistake.  I find it more likely that something has changed in the implementation of fcntl2.h.

Hopefully, someone much smarter than me can look at fcntl2.h, see what it is for, and come up with an idea as to why it causes this error in so many packages.

Thanks,
Michael

---

### Post by RadicalLibre on 2010-12-07
I'm also having the same problem, but trying to build from source a client software called kapitalist ([http://kapitalist.sourceforge.net/](http://kapitalist.sourceforge.net/)) an implementation of the popular game called monopoly.

I'm using Ubuntu 10.10.

¡I hope for a help!

---

