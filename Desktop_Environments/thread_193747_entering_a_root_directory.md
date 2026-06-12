---
title: "entering a root directory"
date: 2006-06-10
forum: Desktop Environments
---

### Post by jordilin on 2006-06-10
Perhaps it's a silly question, but I have a directory which only the user root can access:
drwx------root root directoryname
If I I do a **$ sudo cd directoryname** it says sudo: cd: command not found
so, I don't know how to enter this directory.
thanks

---

### Post by Ramses de Norre on 2006-06-10
You can work around it with sudo -s and then cd'ing, but it's kinda strange sudo cd doesn't work.. I didn't notice that before.

---

