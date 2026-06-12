---
title: "combiling problem"
date: 2005-09-11
forum: Desktop Environments
---

### Post by impeteperry on 2005-09-11
When I tried to compile my programe i got ```
pete@ubuntu:~/myPrograms/pmBlack/pm$ make
make: Warning: File `dlgmain.h' has modification time 6.2e+06 s in the future
g++ -c -pipe -Wall -W -g  -DQT_SHARED -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -o controlfunctions.o controlfunctions.cpp
make: g++: Command not found
make: *** [controlfunctions.o] Error 127
pete@ubuntu:~/myPrograms/pmBlack/pm$
``` I have a g++-3.3 in /usr/bin. i am new to Ubuntu & debian. Any help would be most appreciated.

---

### Post by Leif on 2005-09-11
try sudo apt-get install build-essential, then try again

---

### Post by GoldBuggie on 2005-09-11
The different versions aren't executed by g++, but by g++X.X(X.X beeing the version number)The compilation calls for the general execution of g++ not g++X.X. So what you need to do is

sudo apt-get install g++

Then you are set to go.

---

### Post by impeteperry on 2005-09-11
Thanks Leif & Goldbuggy. It worked, now on to Kdevelop

---

