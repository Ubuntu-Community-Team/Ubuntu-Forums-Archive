---
title: "Qt includes not found"
date: 2009-06-24
forum: General Help
---

### Post by vtco on 2009-06-24
Hi,

I'm trying to install a software for analysis of electrophysiological data. Has been developed by Daniel Wagenaar and use Qt3 libraries. More information:

[http://www.its.caltech.edu/~daw/meabench/]("http://www.its.caltech.edu/%7Edaw/meabench/")

According to his web, the requisites are:
"It should compile on any reasonably recent linux distribution with any 2.4.x or 2.6.x kernel. It requires gcc 2.95 or later and qt 3.0 or later. (Qt 4 is not supported.) Gcc is included with most if not all linux distributions, and can be obtained from many sources, including [www.gnu.org]("http://www.gnu.org"). Qt can be obtained from Trolltech. Most Linux distributions provide both a Qt version 3.x and version 4.x. "

Well, I've compiled and installed in Ubuntu 8.04 but in Ubuntu 8.10 an 9.04 I get this error message when I do ./configure:

"Qt includes not found. Please set QTDIR before running configure again."

I've tried everything. I have qt3 libraries installed, -dev, everything. I also have tried with export QTDIR=/usr/share/qt3/ and with other directories but the problem still remains.

I hope someone can help to solve this.
Thanks

---

### Post by regala on 2009-06-24
> **vtco said:**
> Hi,

I'm trying to install a software for analysis of electrophysiological data. Has ven developed by Daniel Wagenaar and use Qt3 libraries. More information:



```

sudo aptitude install build-essential libqt3-mt-dev

```

Ubuntu, by default, is not installed to give one a development machine. So, usually, C C++ header files are not installed along the libraries (because binaries just wouldn't need them to run).

---

### Post by vtco on 2009-06-24
Thanks a lot. It worked for me.

---

