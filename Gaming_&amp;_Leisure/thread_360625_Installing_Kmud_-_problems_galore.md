---
title: "Installing Kmud - problems galore"
date: 2007-02-13
forum: Gaming &amp; Leisure
---

### Post by zami on 2007-02-13
KMUD - problems galore

I'm trying to get kmud (a mud client) running on my machine, and am following the detailed instructions found here
[http://www.kmud.de/index.html?file=howto.html](http://www.kmud.de/index.html?file=howto.html)
It involves installing some older KDE and QT libraries, and compiling the kmud program.

But I haven't gotten very far at all! 
At 
> 
Now we change into that directory and do the make steps. Notice that the first make step is only for a PC based Linux system. If your system differs read the compile info that comes with the QT-Libraries

$ cd qt-1.44
$ make linux-g++-shared
$ make 

, when I do 
make linux-g++-shared

I get the following error,
```

./propagate configs/linux-g++-shared
cmp: laura/qt-1.44/LICENSE: No such file or directory
cmp: laura/qt-1.44/LICENSE: No such file or directory


   $QTDIR must be set to $PWD (/home/laura/qt-1.44)
   Please read INSTALL


make: *** [linux-g++-shared] Error 1

```

I've since been looking over the install directions for QT itself, and I'm wondering, should I be installing it in a more "normal" fashion, and as root?  If I install this old QT library as root over the whole system, will it cause any conflicts with any newer QT libraries?  

-zami

---

