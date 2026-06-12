---
title: "old i386 linux packages"
date: 2005-01-12
forum: General Help
---

### Post by BlackFenix on 2005-01-12
after install linux-686 (kernel optmized for i686) how i can remove old linux*.386.deb packages ?

aptitude remove linux-386 only remove package linux-386

---

### Post by BlackFenix on 2005-01-13
It is only to enter in /boot and to execute rm in those images and archives of kernel that I do not want?  It is the sufficient?  :-k

---

### Post by wallijonn on 2005-01-13
You can remove the _i386 kernels and modules, but I would re-install the _686 kernel just to be on the safe side so that all the dependecies and system files are all present (check the SPM dependencies and files installed for each kernel).

---

