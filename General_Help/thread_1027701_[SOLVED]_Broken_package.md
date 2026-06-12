---
title: "[SOLVED] Broken package"
date: 2009-01-01
forum: General Help
---

### Post by tegnoto89 on 2009-01-01
I went to install limewirepro via a deb file - it seemed unresponsive after a bit so I forced quit.  It told me I have a broken Java Runtime package, so I went to the package manager and fixed it.

Now I just went to try and install it again, and the package installer says:

Error: Failed to satisfy all dependencies (broken cache)

What should I do?


EDIT:  Fixed it.  Just had some pending items that I installed and it worked fine.

---

### Post by exploder on 2009-01-01
> Error: Failed to satisfy all dependencies (broken cache)

Generally the error message will give you the command needed to fix whatever is broken. Here are some commands to investigate.

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

---

