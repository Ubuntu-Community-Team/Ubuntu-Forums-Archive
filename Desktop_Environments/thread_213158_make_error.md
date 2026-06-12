---
title: "make error"
date: 2006-07-10
forum: Desktop Environments
---

### Post by arthurbarnhouse on 2006-07-10
Trying to install kdocker.  did make in the terminal got the following error:

make: *** No rule to make target `/usr/lib/qt-3.3/mkspecs/default/qmake.conf', n eeded by `Makefile'.  Stop.


What does this mean?

---

### Post by asimon on 2006-07-11
`/usr/lib/qt-3.3/mkspecs/default/qmake.conf' is part of the package [qt3-dev-tools](http://packages.ubuntu.com/dapper/devel/qt3-dev-tools). Do you have this package installed?

---

