---
title: "QPSPManager Install"
date: 2007-06-27
forum: Gaming &amp; Leisure
---

### Post by ric3125 on 2007-06-27
Hello I`am trying to install QPSPManager. I`am following [https://help.ubuntu.com/community/PSP](https://help.ubuntu.com/community/PSP). I have it Uncompress on the desktop. My problem is compile and install the program. qmake worked but when I do a make I get this error.

g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o main.o main.cpp
make: g++: Command not found
make: *** [main.o] Error 127

---

### Post by po0f on 2007-06-27
ric3125,

Try installing [build-essential](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=build-essential&searchon=names&subword=1&version=all&release=all).

[EDIT]

After looking at the page you linked, it looks like the author forgot to list build-essential as a dependency; oh well.  :)

---

### Post by ric3125 on 2007-06-29
Ok got the build-essential installed. Now it is giving me this, after I do  a qmake, make.


make: Nothing to be done for `first'.

---

### Post by ric3125 on 2007-06-30
Bump

---

### Post by ric3125 on 2007-07-03
Bump

---

### Post by Ciego on 2007-09-30
I have the same issues trying to get this to work.

---

### Post by Ciego on 2007-09-30
Actually .... I just noticed that the bin file was created but the install just didn't work.    I don't know if the same thing happened for you but if it did, you can issue the following command to launch the program
```

$ ./bin/QPSPManager
```

You need to issue the command from the directory where you were compiling from.

---

