---
title: "How do I install an application so all users on a computer can use it?"
date: 2009-02-17
forum: General Help
---

### Post by 3pinner on 2009-02-17
I have 3 users on my desktop, and need to make an application available to all of them.
so how do I do that??

Can I do this in WINE?

Thanks!

---

### Post by kanikilu on 2009-02-17
What application? How was it installed (compiling, dpkg -i, apt-get)?

---

### Post by 3pinner on 2009-02-17
The critical one I need is installed in WINE, so it is a windows program that I would like to make avialable to all the users, without having to install it 3 times.

---

### Post by mb_webguy on 2009-02-17
You could put the application folder in a common location then put a symlink to this location in the users' "~/.wine/drive_c/Program Files" directory...

---

