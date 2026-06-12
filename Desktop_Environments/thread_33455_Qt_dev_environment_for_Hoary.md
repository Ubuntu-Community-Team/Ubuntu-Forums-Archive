---
title: "Qt dev environment for Hoary?"
date: 2005-05-10
forum: Desktop Environments
---

### Post by jfdill_2 on 2005-05-10
What packages should I have installed to build KDE / Qt apps on Hoary?

I'm trying to build [evolvotron](http://www.bottlenose.demon.co.uk/share/evolvotron/index.htm)  and I'm getting tons of *undefined reference* errors in the linking stage.  I'm guessing that I need to install some package with headers, or have incompatible versions of something installed.  What packages should I have installed in order to build KDE apps?

I installed the following to start, with all prerequisites and dependencies:

libqt3-dev
gcc
g++
autoconf
automake
libtool

and defined QTDIR=/usr/share/qt3

---

### Post by jfdill_2 on 2005-05-11
Got it:

remove libqt3-dev
install qt3-apps-dev

I also installed libqt3-compat-headers for good measure, but I'm not sure that was necessary.

---

