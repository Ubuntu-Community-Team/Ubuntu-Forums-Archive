---
title: "KDE 5.4.3 Upgrade - Important package will be removed!"
date: 2006-08-05
forum: Desktop Environments
---

### Post by daller on 2006-08-05
Hi there,

Is there a problem with removing kdelibs-bin???

According to "apt-cache show kdelibs-bin" - the package is pretty important!

```
Description: core binaries for all KDE applications
 This package contains all the common binaries with are used by KDE
 applications. You need these binaries to run KDE applications.
 .
 Several scripts included in kdebase-bin, related to the handling of SMB
 and NFS shares, require the perl-suid package to work properly.
 .
 This package is part of KDE, and a component of the KDE libraries module.
 See the 'kde' and 'kdelibs' packages for more information.

```

What should I do?

---

### Post by sjhstorm on 2006-08-05
I have just upgraded to 3.5.4 today, kdelibs-bin does get removed but a new versions of kdelibs provides the binaries. All went well with my upgrade.

---

