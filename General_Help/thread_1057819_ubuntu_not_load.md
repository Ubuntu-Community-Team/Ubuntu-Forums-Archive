---
title: "ubuntu not load"
date: 2009-02-02
forum: General Help
---

### Post by alis313 on 2009-02-02
when ubuntu is loading after splashy it say " 
GDM could not write to your authorization file. This could mean that you are out of disk space orthat your home directory could not be opened for writing. In any case, it is not possible to login. Please contact your system administrator. "
why?

---

### Post by taurus on 2009-02-02
At the GUI login screen, press <Ctrl><Alt>F2 and log in with your username and password.  Then, look at your disk space to make sure it's not max out.

```
df -h
```
Also, look at the ownership of your files to be sure you are still the owner.

```
ls -la | more
```
Hit the space key for the next 24 lines.

---

