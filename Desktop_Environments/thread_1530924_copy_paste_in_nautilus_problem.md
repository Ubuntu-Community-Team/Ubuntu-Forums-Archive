---
title: "copy paste in nautilus problem"
date: 2010-07-14
forum: Desktop Environments
---

### Post by AlexDS on 2010-07-14
I need to copy/paste **/home/alexds/Desktop/gimp/2.0/python** directory to **/usr/lib/gimp/2.0**.
I wanted to do that in nautilus but he says error: i have no permission

how can i do that?

---

### Post by stinkeye on 2010-07-14
```
gksu nautilus
``` will open nautilus as root and have the appropriate pemissions to copy to /usr/lib/gimp/2.0

---

### Post by AlexDS on 2010-07-14
thank you very much!

---

### Post by stinkeye on 2010-07-14
No problem.
You can also add an entry to the right click nautilus menu, **Open as administrator**
by installing **nautilus-gksu**
Search for and download in the software centre.

This will allow you to open files and folders as root.
You should only use if instructed to do so(eg edit a certain file owned by root) or you know what your doing.
Most files and folders outside your home directory are owned by root for security and stability of your system.

---

