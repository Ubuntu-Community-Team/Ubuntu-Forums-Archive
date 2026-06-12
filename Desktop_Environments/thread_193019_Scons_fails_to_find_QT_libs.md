---
title: "Scons fails to find QT libs"
date: 2006-06-09
forum: Desktop Environments
---

### Post by ktulu1115 on 2006-06-09
I'm trying to compile madman, as the version in the repos crashes when I load my MP3s.

```
$ ./scons.py
scons: Reading SConscript files ...
Checking for qt at /usr/lib/ (with lib) failed
Checking for qt-mt at /usr/lib/ (with lib) failed
Checking for qt at /usr/share/qt3 (with lib) failed
Checking for qt-mt at /usr/share/qt3 (with lib) failed
Checking for qt at /usr/share/qt (with lib) failed
Checking for qt-mt at /usr/share/qt (with lib) failed
Checking for qt at /usr (with lib) failed
Checking for qt-mt at /usr (with lib) failed
Checking for qt at /usr/local (with lib) failed
Checking for qt-mt at /usr/local (with lib) failed
Checking for qt at /usr/lib/qt3 (with lib) failed
Checking for qt-mt at /usr/lib/qt3 (with lib) failed
Checking for qt at /usr/lib/qt (with lib) failed
Checking for qt-mt at /usr/lib/qt (with lib) failed
Checking for qt at /usr/lib/ (with lib64) failed
Checking for qt-mt at /usr/lib/ (with lib64) failed
Checking for qt at /usr/share/qt3 (with lib64) failed
Checking for qt-mt at /usr/share/qt3 (with lib64) failed
Checking for qt at /usr/share/qt (with lib64) failed
Checking for qt-mt at /usr/share/qt (with lib64) failed
Checking for qt at /usr (with lib64) failed
Checking for qt-mt at /usr (with lib64) failed
Checking for qt at /usr/local (with lib64) failed
Checking for qt-mt at /usr/local (with lib64) failed
Checking for qt at /usr/lib/qt3 (with lib64) failed
Checking for qt-mt at /usr/lib/qt3 (with lib64) failed
Checking for qt at /usr/lib/qt (with lib64) failed
Checking for qt-mt at /usr/lib/qt (with lib64) failed
```

Tried passing 'qt_directory=' a few different paths as well but no luck - the README said you need the following packages:

- Qt. [[http://www.trolltech.com]](http://www.trolltech.com])
  Version 3.2.x tested, others might work, too. (patches welcome)
  [Debian pacakge: libqt3-mt-dev, NOT libqt3-dev]

Installed that package, but no luck...  any ideas?  AMD64 if it makes any difference...

---

