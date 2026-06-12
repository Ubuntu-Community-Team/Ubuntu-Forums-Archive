---
title: "How to specify which gcc version to use??"
date: 2005-12-30
forum: General Help
---

### Post by bigblop on 2005-12-30
I have an old program the will not compile with gcc 4.0 when I type "make"

is there someway to tell make to use gcc 3.3 instead?

---

### Post by MetalMusicAddict on 2005-12-30
Maybe **CC=gcc-3.3** before **make**? I just compiled the nVidia drivers and I had to **CC=gcc-3.4** 1st.

---

### Post by bigblop on 2005-12-30
CC=gcc-3.3

does nothing it still uses gcc-4.0

---

### Post by cstudent on 2005-12-30
I think it might be:

CC=gcc-3.3
export CC

---

### Post by bigblop on 2005-12-30
does that do it permanently or only for the current session?

---

### Post by bigblop on 2005-12-30
..no that did not change anything either

---

### Post by cstudent on 2005-12-30
Not implying anthing here, but did you install the 3.3 libraries?

---

### Post by bigblop on 2005-12-30
jep. Need to reinstall Ubuntu I guess and then not choose gcc 4.0

---

### Post by gert cuykens on 2005-12-30
first off why does the kernel get compiled in a other gcc version then the aplications in ubuntu :confused: 

gert@F53:~$ cat /proc/version
Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Thu Dec 22 11:37:10 UTC 2005
gert@F53:~$

ps try this

#!/bin/sh
#apt-get install build-essential
#apt-get install linux-headers-`uname -r`
#cat /proc/version
#apt-get install gcc-3.4
#ln -s /usr/bin/gcc-3.4 /usr/bin/gcc

---

### Post by kaamos on 2005-12-30
> jep. Need to reinstall Ubuntu I guess and then not choose gcc 4.0
Now that sound like a REALLY bad idea. Ubuntu installs with 4.0

About compiling a kernel, look here:
Look here: [http://ubuntuforums.org/showthread.php?t=85064](http://ubuntuforums.org/showthread.php?t=85064)

> 6) su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
If you want to use 3.3 make sure you have both gcc-3.3 and gcc-3.3-base installed.

---

### Post by robotgeek on 2005-12-30
[QUOTE=kaamos]Now that sound like a REALLY bad idea. Ubuntu installs with 4.0

About compiling a kernel, look here:
Look here: [http://ubuntuforums.org/showthread.php?t=85064](http://ubuntuforums.org/showthread.php?t=85064)[/QUOTE]

No need to enable root for anything. 

```

export CC=/usr/bin/gcc-3.4

```

That should be enough to do it.

---

### Post by bigblop on 2005-12-30
nope that did not work either (I have gcc-3.3 and gcc-3.3-base installed.):

mos@ubuntu:~$ su
Password:
root@ubuntu:/home/mos# CC=gcc-3.3
root@ubuntu:/home/mos# export CC
root@ubuntu:/home/mos# exit
exit
mos@ubuntu:~$ CC=gcc-3.3
mos@ubuntu:~$ export CC
mos@ubuntu:~$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada, treelang --prefix=/usr --with-gxx-include-dir=/usr/include/c++/4.0.2 --enable-sh ared --with-system-zlib --libexecdir=/usr/lib --enable-nls --without-included-ge ttext --enable-threads=posix --program-suffix=-4.0 --enable-__cxa_atexit --enabl e-libstdcxx-allocator=mt --enable-clocale=gnu --enable-libstdcxx-debug --enable- java-gc=boehm --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib /jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --enable-chec king=release i486-linux-gnu
Thread model: posix
gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
mos@ubuntu:~$

as can  be seen from the last line gcc is stil 4.0.2...

---

### Post by bigblop on 2005-12-30
[QUOTE=robotgeek]No need to enable root for anything. 

```

export CC=/usr/bin/gcc-3.4

```

That should be enough to do it.[/QUOTE]


that did not work either:

mos@ubuntu:~$ export CC=/usr/bin/gcc-3.3
mos@ubuntu:~$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --with-gxx-include-dir=/usr/include/c++/4.0.2 --enable-shared --with-system-zlib --libexecdir=/usr/lib --enable-nls --without-included-gettext --enable-threads=posix --program-suffix=-4.0 --enable-__cxa_atexit --enable-libstdcxx-allocator=mt --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-gc=boehm --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
mos@ubuntu:~$

---

### Post by robotgeek on 2005-12-30
Your ./configure script will take gcc from the CC variable. gcc -v will still point to the newest version

---

### Post by kaamos on 2005-12-30
(edit: too slow.)

---

### Post by bigblop on 2005-12-30
there is no configure script only a Makefile. When I run that I get:

In file included from fig2dev.h:25,
                 from fig2dev.c:27:
/usr/lib/gcc/i486-linux-gnu/4.0.2/include/varargs.h:4:2: error: #error "GCC no longer implements <varargs.h>."
/usr/lib/gcc/i486-linux-gnu/4.0.2/include/varargs.h:5:2: error: #error "Revise your code to use <stdarg.h>."
make[1]: *** [fig2dev.o] Error 1
make[1]: Leaving directory `/home/johs/apps/transfig.3.2.4/fig2dev'
make: *** [all] Error 2
johs@ubuntu:~/apps/transfig.3.2.4$

---

### Post by robotgeek on 2005-12-30
Ughh, okay...
```

sudo rm /usr/bin/gcc
sudo ln -s /usr/bin/gcc-3.4 /usr/bin/gcc

```

Finish your compile, then restore the original symlink
```

sudo rm /usr/bin/gcc
sudo ln -s /usr/bin/gcc-4.0 /usr/bin/gcc

```

---

### Post by ulli.winter on 2008-06-20
thanks robotgeek,
seemed to work...

---

