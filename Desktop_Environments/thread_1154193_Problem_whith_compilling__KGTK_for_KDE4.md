---
title: "Problem whith compilling  KGTK for KDE4"
date: 2009-05-09
forum: Desktop Environments
---

### Post by mhspace on 2009-05-09
KGTK for KDE3 compiled sucsessful. but when I'm trying to compile it for KDE4, the cmake fails.

> cmake .. -DCMAKE_INSTALL_PREFIX=/usr -DKGTK_KDE4=true -DKGTK_QT4=true -DKGTK_GTK2=false
-- The C compiler identification is GNU
-- The CXX compiler identification is unknown
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was notfound.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Looking for getpeereid
-- Looking for getpeereid - not found
** INFORMATION: Compiling Qt4/KDE4, Qt3/KDE3 disabled
-- Looking for Q_WS_X11
-- Looking for Q_WS_X11 - not found.
-- Looking for Q_WS_WIN
-- Looking for Q_WS_WIN - not found.
-- Looking for Q_WS_QWS
-- Looking for Q_WS_QWS - not found.
-- Looking for Q_WS_MAC
-- Looking for Q_WS_MAC - not found.
** ERROR      : Could not locate , KDialogD for KDE4 will not be built.
** ERROR      : Could not locate Qt4 headers, Qt4 LD_PRELOAD library will not be built.
** INFORMATION: Using installation prefix: /usr
-- Configuring incomplete, errors occurred!What Qt4/KDE4 headers?

---

### Post by L_V on 2009-09-13
According to [_KDE File Chooser for all GTK apps_](https://bugs.launchpad.net/ubuntu/+source/kubuntu-meta/+bug/281834), there is not yet any working Kgtk package compatible with KDE4.3.

The problem is that compiling this small [_Kgtk package_](http://amarok.kde-apps.org/content/show.php/KGtk+%28Use+KDE+Dialogs+in+Gtk+Apps%29?content=36077) requires **137MB** of extra packages, which is not very user-friendly for something which should be part of any KDE distribution.

Does somebody know why Kgtk is still in discussion at ubuntu ?
Thanks.

---

### Post by L_V on 2009-09-15
[quote=Chettagadeng]I've built a .deb file from the source, it works for me on Feisty...
Attached Files
File Type: deb 	kgtk_0.8-1_i386.deb (63.7 KB, 199 views)[/quote]

Compilation of Kgtk for each ubuntu release is a nightmare.
Does somebody know where to find a Kgtk package for Karmic ?
Thanks.

---

### Post by Magnesium on 2009-12-08
> **L_V said:**
> Compilation of Kgtk for each ubuntu release is a nightmare.
Does somebody know where to find a Kgtk package for Karmic ?
Thanks.

Hey folks, if anyone is still listening....there is a PPA with kgtk in it. It says it is for Jaunty, but it works perfectly on my Kubuntu Karmic.

The PPA is at [https://launchpad.net/~kgtk/+archive/ppa](https://launchpad.net/~kgtk/+archive/ppa). You'll have to use the jaunty version (cause there is no Karmic version), but once you add it and do sudo apt-get update, just type

```
sudo apt-get install kgtk
```

Mg

---

