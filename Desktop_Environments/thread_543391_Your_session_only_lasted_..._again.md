---
title: "Your session only lasted ... again"
date: 2007-09-05
forum: Desktop Environments
---

### Post by zipo99 on 2007-09-05
this time error is 
x-session-manager: error while loading shared libraries: libavahi-glib.so.1: cannot open shared object file: no such file or directory

---

### Post by kidders on 2007-09-05
Hi there,

That error is reasonably self-explanatory. It seems like libavahi-glib.so.1 (which is an mDNS-related library) doesn't exist. You'd probably get a similar error if the file was corrupted or otherwise unusable.

I would suggest identifying an installed package that contains the file in question, and reinstalling it. If that doesn't fix the problem, it would certainly eliminate a few possible causes.

---

