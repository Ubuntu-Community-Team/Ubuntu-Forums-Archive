---
title: "Dashboard CVS"
date: 2006-07-22
forum: Desktop Environments
---

### Post by mattman on 2006-07-22
Has anyone gotten this to install on Dapper? I tried and it fails because of multiple missing Makefile.in files. Does anyone know of a solution for this?](*,)  Any help would be appreciated.

---

### Post by mattman on 2006-07-22
Well I solved the first problem by installing automake 1.4. Now I'm receiving the following error.
make[2]: Entering directory `/home/matt/dashboard/dashboard/engine'
/bin/sh ../../mkinstalldirs /usr/bin
/bin/sh: ../../mkinstalldirs: No such file or directory
make[2]: *** [install-binSCRIPTS] Error 127
make[2]: Leaving directory `/home/matt/dashboard/dashboard/engine'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/matt/dashboard/dashboard/engine'
make: *** [install-recursive] Error 1
](*,)

---

