---
title: "Kernel not updating right"
date: 2009-11-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chabos9 on 2009-11-29
I tried using apt-get to update the kernel.  It said my kernel was at the latest version.  But uname -r still returns 2.6.28-11-generic.  In /lib/modules, there is now three folders.  2.6.28-11-generic, 2.6.31-14-generic, and 2.6.31-14-386, which I installed hoping it would fix the problem (it didn't).  The problem is that my system seems to be using 2.6.31-14-generic, because 2.6.28-11-generic doesn't contain things like the source file, but my system thinks its using 2.6.28-11-generic.  How do I fix this?

---

### Post by chabos9 on 2009-11-29
Never mind.  I ran the update manager and it seems to be working now.  I think it might have been a problem with menu.lst.

---

