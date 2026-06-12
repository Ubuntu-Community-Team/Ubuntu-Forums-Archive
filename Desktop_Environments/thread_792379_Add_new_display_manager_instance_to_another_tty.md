---
title: "Add new display manager instance to another tty?"
date: 2008-05-12
forum: Desktop Environments
---

### Post by nchase on 2008-05-12
How do you start up a new and separate display manager instance on another tty (ctrl + alt + [f1-f7])?

---

### Post by RAOF on 2008-05-13
This is exactly what fast user switching does.  Each user has their own X server running on a different TTY (except they use 7, 8, 9, etc).  I'm not sure what happens if you fast-user-switch and login as yourself again; I presume it works correctly.

---

