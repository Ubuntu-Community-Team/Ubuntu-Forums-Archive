---
title: "Complilation error"
date: 2009-01-21
forum: Education &amp; Science
---

### Post by void_void on 2009-01-21
i am using ubuntu 8.4
net beans 6.5 IDE
my c code is 

#include "stdio.h"

main()
{
	printf("hello\n");
        return 0;
}

when i try to run it it gives me the following error message
i have set project property->c compiler>include directory 
to a dir containing stdio.h file which i've downloaded from 

[http://www.koders.com/c/fidBA34B16D0731D0AE92D06DEAC3B0762F71552E57.aspx?s=download+unistd.h](http://www.koders.com/c/fidBA34B16D0731D0AE92D06DEAC3B0762F71552E57.aspx?s=download+unistd.h)

while in the other m/c with same configuration i get following message


Running "/usr/bin/make  -f Makefile CONF=Debug" in /home/npadharia/NetBeansProjects/Application_1

/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .build-conf
make[1]: Entering directory `/home/npadharia/NetBeansProjects/Application_1'
/usr/bin/make  -f nbproject/Makefile-Debug.mk dist/Debug/GNU-Linux-x86/application_1
make[2]: Entering directory `/home/npadharia/NetBeansProjects/Application_1'
mkdir -p dist/Debug/GNU-Linux-x86
gcc     -o dist/Debug/GNU-Linux-x86/application_1 build/Debug/GNU-Linux-x86/prac.o 
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
make[2]: *** [dist/Debug/GNU-Linux-x86/application_1] Error 1
make[2]: Leaving directory `/home/npadharia/NetBeansProjects/Application_1'
make[1]: *** [.build-conf] Error 2
make[1]: Leaving directory `/home/npadharia/NetBeansProjects/Application_1'
make: *** [.build-impl] Error 2

Build failed. Exit value 2.

Running "/usr/bin/make  -f Makefile CONF=Debug" in /home/jjoshi/NetBeansProjects/hi

/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .build-conf
make[1]: Entering directory `/home/jjoshi/NetBeansProjects/hi'
/usr/bin/make  -f nbproject/Makefile-Debug.mk dist/Debug/GNU-Linux-x86/hi
make[2]: Entering directory `/home/jjoshi/NetBeansProjects/hi'
mkdir -p build/Debug/GNU-Linux-x86
rm -f build/Debug/GNU-Linux-x86/hi.o.d
gcc    -c -g -I../../Desktop/c\ lib -MMD -MP -MF build/Debug/GNU-Linux-x86/hi.o.d -o build/Debug/GNU-Linux-x86/hi.o hi.c
In file included from hi.c:2:
../../Desktop/c lib/stdio.h:46:27: warning: crtdll/stddef.h: No such file or directory
In file included from hi.c:2:
../../Desktop/c lib/stdio.h:176: error: expected declaration specifiers or ‘...’ before ‘size_t’
../../Desktop/c lib/stdio.h:198: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
../../Desktop/c lib/stdio.h:212: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
../../Desktop/c lib/stdio.h:213: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
../../Desktop/c lib/stdio.h:214: error: expected ‘)’ before ‘*’ token
../../Desktop/c lib/stdio.h:215: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
../../Desktop/c lib/stdio.h:216: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
../../Desktop/c lib/stdio.h:217: error: expected ‘)’ before ‘*’ token
../../Desktop/c lib/stdio.h:228: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
../../Desktop/c lib/stdio.h:229: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
../../Desktop/c lib/stdio.h:230: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
../../Desktop/c lib/stdio.h:250: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fgetwc’
../../Desktop/c lib/stdio.h:251: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fputwc’
../../Desktop/c lib/stdio.h:252: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘getwc’
../../Desktop/c lib/stdio.h:253: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ungetwc’
../../Desktop/c lib/stdio.h:255: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘_filwbuf’
../../Desktop/c lib/stdio.h:256: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘_flswbuf’
../../Desktop/c lib/stdio.h:278: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fread’
../../Desktop/c lib/stdio.h:280: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fwrite’
make[2]: *** [build/Debug/GNU-Linux-x86/hi.o] Error 1
make[2]: Leaving directory `/home/jjoshi/NetBeansProjects/hi'
make[1]: *** [.build-conf] Error 2
make[1]: Leaving directory `/home/jjoshi/NetBeansProjects/hi'
make: *** [.build-impl] Error 2

Build failed. Exit value 2.

---

