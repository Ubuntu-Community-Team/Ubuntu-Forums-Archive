---
title: "qtfprot-0.2.1c - Installing"
date: 2005-12-12
forum: Desktop Environments
---

### Post by Spook_Man on 2005-12-12
Hello,
      I'm currently testing Kubuntu as an alternative to Suse (what can I say, Adept is a feature that is hard to pass up on; but an update for this would be the ability to search for something a package contains, Yast has this feature).

     Anyway, I've been able to install F-Prot and am attempting to install qtfprot.  I've downloaded both the .deb package as well as the tar.

    If I attempt to install using the tar, after the ./configure, I get the following error:
**checking for Qt... configure: error: Qt (>= Qt 3.1 (20021021)) (headers and libraries) not found. Please check your installation!**

     If I attempt to install using the .deb package, I get the following error:
[B]qtfprot depends on kdelibs4 (>= 4:3.3.1); however:  Package kdelibs4 is not installed.
qtfprot depends on libqt3c102-mt (>= 3:3.3.3); however: Package libqt3c102-mt is not installed.
[/B]

     Ive installed kdelibs4, but the libqt3c102-mt package is not found.  Any ideas?    Thanks.. -Jeff

---

### Post by mlomker on 2005-12-12
[QUOTE=Spook_Man]    If I attempt to install using the tar, after the ./configure, I get the following error:
**checking for Qt... configure: error: Qt (>= Qt 3.1 (20021021)) (headers and libraries) not found. Please check your installation!**
[/QUOTE]

Try installing the **kde-devel** package.

---

