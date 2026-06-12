---
title: "No programs will install...?"
date: 2008-12-27
forum: General Help
---

### Post by Troniknz on 2008-12-27
Hey, I am using Ubuntu 8.10 and now when i go to install programs with Add/remove it comes up with:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

can anybody help?

Thanks
Troniknz

---

### Post by snova on 2008-12-27
Go to Applications -> Accessories -> Terminal. Type this in and press enter:

> sudo dpkg --configure -a

Type your password when requested (it will not show).

---

### Post by Troniknz on 2008-12-27
Yay, it worked, thank you heaps!

---

