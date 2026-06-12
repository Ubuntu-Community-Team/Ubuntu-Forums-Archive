---
title: "error compiling bespin"
date: 2009-11-29
forum: Desktop Environments
---

### Post by Pasdar on 2009-11-29
I get the following error when attempting ./configure for bespin theme:

> ==================== Bespin interactive configuration ====================

    Seems you have cmake.
    In addition to the style, you can have a KWin decoration,
    a mac-like menu plasmoid and config plugins IFF you have KDE....

--> Do you want to compile with KDE support? [Y/n]
-- INFO: Amarok Hacks disabled, not compiling support for amarok hacks.
-- WARNING: *** KDE4 not found, just the style will be built ***
-- INFO: XRender was found - kwin deco & FX via GPU available!
CMake Error at blib/CMakeLists.txt:42 (install):
  install TARGETS given no LIBRARY DESTINATION for shared library target
  "QtBespin".


-- Configuring incomplete, errors occurred!

Any ideas? I'm doing this on KDE 4.3.2

---

### Post by ElSlunko on 2009-12-01
In the install readme there are a list of libs you'll need. Also, when I got that error it said I had cmake but I didn't, I had to sudo apt-get install cmake.

---

