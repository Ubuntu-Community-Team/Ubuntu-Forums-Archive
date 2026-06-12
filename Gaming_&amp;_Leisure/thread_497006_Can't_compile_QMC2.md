---
title: "Can't compile QMC2"
date: 2007-07-09
forum: Gaming &amp; Leisure
---

### Post by Juan_VCS on 2007-07-09
This is the *make* output:

```
g++ -c -pipe -O2 -w -D_REENTRANT  -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -Iminizip -I. -I. -o qmc2main.o qmc2main.cpp
qmc2main.cpp: In function &#8216;int main(int, char**)&#8217;:
qmc2main.cpp:1450: error: &#8216;MAJOR&#8217; was not declared in this scope
qmc2main.cpp:1450: error: &#8216;MINOR&#8217; was not declared in this scope
make: *** [qmc2main.o] Error 1
```

---

