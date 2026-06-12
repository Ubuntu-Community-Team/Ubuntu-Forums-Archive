---
title: "RPM Files"
date: 2005-12-09
forum: Desktop Environments
---

### Post by jrok311 on 2005-12-09
Does this distro have RPM file support?

---

### Post by Bachstelze on 2005-12-09
No. Since it is debian-based, it supports .deb packages only. But you can use a tool named alien to convert RPMs to .deb. It works in most cases (but not all)

---

### Post by ogregore on 2005-12-09
Jrok

You may have to apt-get "alien" package then from the terminal

             $ sudo alien -i <package name>.rpm

Cheers
Ogre

---

