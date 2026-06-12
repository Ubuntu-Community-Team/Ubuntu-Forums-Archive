---
title: "Exalt Install for e17"
date: 2007-08-07
forum: Desktop Environments
---

### Post by onthefritz on 2007-08-07
I am having a problem installing exalt for e17. I followed the instructions at [http://ubuntuforums.org/showthread.php?t=473331](http://ubuntuforums.org/showthread.php?t=473331) that were: (thank you watchwolf)
```
cvs -z3 -d:pserver:anonymous@cvs.exalt.berlios.de:/cvsroot/exalt co exalt
cd exalt/libexalt
./autogen.sh
make
sudo make install
cd ../exalt
./autogen.sh
make
sudo make install
```

I get the following error when running ./autogen.sh in the exailt directory.

```
login@computer:~/Installers/exalt/exalt$ ./autogen.sh 
Running aclocal...
configure.in:82: warning: macro `AM_GNU_GETTEXT' not found in library
configure.in:83: warning: macro `AM_GNU_GETTEXT_VERSION' not found in library
Running autoheader...
Running autoconf...
configure.in:82: error: possibly undefined macro: AM_GNU_GETTEXT
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:83: error: possibly undefined macro: AM_GNU_GETTEXT_VERSION

```

I think I am missing a lib or something but I'm not sure what lib.

---

### Post by earlycj5 on 2007-10-17
Try searching synaptic for gettext and installing that.

---

