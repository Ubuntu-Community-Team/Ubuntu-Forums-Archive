---
title: "QtGui Error When Trying to Install an Old Version of MAME"
date: 2019-02-08
forum: Emulators
---

### Post by autogolazzojr on 2019-02-08
Hello. I've been trying to install a modded version of MAME from 2015. The version can be found at [https://github.com/osresearch/mame](https://github.com/osresearch/mame). Unfortunately, when I try to install it, I run into this problem. I installed this program last year on an older machine, and I had the same error. I fixed the problem by manually finding QtGui and moving it to where it was looking. This doesn't seem to work now. What should I do? Here is the error: 
[https://i.imgur.com/AFCCnLf.jpg](https://i.imgur.com/AFCCnLf.jpg)

---

### Post by deadflowr on 2019-02-08
*Thread moved to **Emulators***

Could it be an issue of Ubuntu using qt5 instead of qt4?

---

### Post by autogolazzojr on 2019-02-08
It most likely is. I installed qt4-default and libqt4-dev and it still didn't work. I then copied all the contents of /usr/include/qt4 to /usr/include
It got much further but then ran into a BUNCH of undefined reference messages that look like this:
[https://i.imgur.com/gb8lZj2.jpg](https://i.imgur.com/gb8lZj2.jpg)

---

