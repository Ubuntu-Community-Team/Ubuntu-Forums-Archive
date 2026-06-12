---
title: "/usr/bin/ld: cannot find -lncursesw &quot;libcursesw&quot;"
date: 2014-08-07
forum: Desktop Environments
---

### Post by ajaygautam2 on 2014-08-07
Hi,
I am compiling a 3rd party code on Ubuntu Machine and i am getting following error:
/usr/bin/gcc -DCURSES_LOC="<ncurses.h>" -DLOCALE  -g -O2 -m32  conf.o  zconf.tab.o -lncursesw -o conf
/usr/bin/ld: cannot find -lncursesw
collect2: ld returned 1 exit status

Already i did below:
1. Installed      sudo apt-get install libncursesw5-dev
2. Created soft link also:
    sudo ln -s /lib/x86_64-linux-gnu/libncursesw.so.5 /lib/x86_64-linux-gnu/libcursesw.so
    sudo ln -s /lib/x86_64-linux-gnu/libncursesw.so.5 /usr/lib/x86_64-linux-gnu/libcursesw.so
    sudo ln -s /lib/x86_64-linux-gnu/libncursesw.so.5 /usr/lib/libcursesw.so

still i am getting same above error.
Can anybody please help me?

Thanks
Ajay

---

### Post by steeldriver on 2014-08-07
Since you are building a 32-bit executable (-m32), you probably need to explicitly install the libncursesw5-dev:i386 package, no?

Manually symlinking things should not be necessary

---

### Post by ajaygautam2 on 2014-08-07
Thanks,
That problem is solved but after some time again i am getting:
Build dependency: Please install ncurses. (Missing libncurses.so or ncurses.h) 

even i installed :
sudo apt-get install libncurses5-dev:i386
and created soft link also.

---

