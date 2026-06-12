---
title: "Athlon XP on the fly multiplier change"
date: 2006-05-01
forum: Desktop Environments
---

### Post by supermarchino on 2006-05-01
[http://www.mars.dti.ne.jp/~daitei/k7mctrl/](http://www.mars.dti.ne.jp/~daitei/k7mctrl/)

:( don't even know how to install it

any suggesions / different choiches?

---

### Post by Stormbringer on 2006-05-01
Ahh... Japanese...
Lets Google create a [translation]("http://translate.google.com/translate?u=http%3A%2F%2Fwww.mars.dti.ne.jp%2F%7Edaitei%2Fk7mctrl%2F&langpair=ja%7Cen&hl=de&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools") (not very accurate, but one should be able to understand the meaning)

You cannot simply install the program - you need to compile it!

- Download the archive and unpack it into your home folder.
- Make sure you have the basic packages needed for compiling installed
  (sudo apt get install gcc build-essential)
- Open a terminal and change into the directory where you extracted k7mctrl

There's a makefile - so simply type "make" and see if everything goes well.

If any requirement is missing (i.e. TK development libraries for the GUI) it will drop you an error notice ... simply post the error message here, maybe we can figure out what's missing.

BTW: Are you _really_ sure your CPU actually supports frequency scaling/switching? The only AMD K7 CPU I know about to support this feature is the Athlon XP-M (or pin-modded Athlon XP's).

Storm.

---

### Post by supermarchino on 2006-05-11
[QUOTE=Stormbringer]Ahh... Japanese...
Lets Google create a [translation]("http://translate.google.com/translate?u=http%3A%2F%2Fwww.mars.dti.ne.jp%2F%7Edaitei%2Fk7mctrl%2F&langpair=ja%7Cen&hl=de&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools") (not very accurate, but one should be able to understand the meaning)

You cannot simply install the program - you need to compile it!

- Download the archive and unpack it into your home folder.
- Make sure you have the basic packages needed for compiling installed
  (sudo apt get install gcc build-essential)
- Open a terminal and change into the directory where you extracted k7mctrl

There's a makefile - so simply type "make" and see if everything goes well.

If any requirement is missing (i.e. TK development libraries for the GUI) it will drop you an error notice ... simply post the error message here, maybe we can figure out what's missing.

BTW: Are you _really_ sure your CPU actually supports frequency scaling/switching? The only AMD K7 CPU I know about to support this feature is the Athlon XP-M (or pin-modded Athlon XP's).

Storm.[/QUOTE]

```

marco@server:~/Desktop/k7mctrl-0.2a$ sudo make
Password:
make -C lib
make[1]: Entering directory `/home/marco/Desktop/k7mctrl-0.2a/lib'
gcc  -O2  -c argfunc.c -o argfunc.o
gcc  -O2  -c getword.c -o getword.o
ar r libmiscio.a argfunc.o getword.o
ar: creating libmiscio.a
gcc  -O2  -c devmsr.c -o devmsr.o
ar r libdevmsr.a devmsr.o
ar: creating libdevmsr.a
make[1]: Leaving directory `/home/marco/Desktop/k7mctrl-0.2a/lib'
make -C cmd
make[1]: Entering directory `/home/marco/Desktop/k7mctrl-0.2a/cmd'
gcc -c -O2 -g -I../lib k7mctrl.c
k7mctrl.c: In function 'main':
k7mctrl.c:161: warning: incompatible implicit declaration of built-in function 'exit'
k7mctrl.c:169: warning: incompatible implicit declaration of built-in function 'exit'
make -C ../lib
make[2]: Entering directory `/home/marco/Desktop/k7mctrl-0.2a/lib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/marco/Desktop/k7mctrl-0.2a/lib'
gcc -o k7mctrl k7mctrl.o -L../lib -lmiscio -ldevmsr
make[1]: Leaving directory `/home/marco/Desktop/k7mctrl-0.2a/cmd'
make -C tk
make[1]: Entering directory `/home/marco/Desktop/k7mctrl-0.2a/tk'
gcc -O2 -I/usr/include/tcl8.4 -I../lib -c tkk7m.c -o tkk7m.o
tkk7m.c:7:17: error: tcl.h: No such file or directory
tkk7m.c:8:16: error: tk.h: No such file or directory
In file included from tkk7m.c:22:
../lib/miscio.h:59: error: syntax error before '*' token
../lib/miscio.h:65: error: syntax error before '*' token
../lib/miscio.h:65: warning: data definition has no type or storage class
tkk7m.c:57: error: syntax error before 'argTable'
tkk7m.c:58: warning: braces around scalar initializer
tkk7m.c:58: warning: (near initialization for 'argTable[0]')
tkk7m.c:58: warning: initialization makes integer from pointer without a cast
tkk7m.c:58: error: 'TK_ARGV_END' undeclared here (not in a function)
tkk7m.c:58: warning: excess elements in scalar initializer
tkk7m.c:58: warning: (near initialization for 'argTable[0]')
tkk7m.c:58: warning: excess elements in scalar initializer
tkk7m.c:58: warning: (near initialization for 'argTable[0]')
tkk7m.c:58: warning: excess elements in scalar initializer
tkk7m.c:58: warning: (near initialization for 'argTable[0]')
tkk7m.c:59: warning: excess elements in scalar initializer
tkk7m.c:59: warning: (near initialization for 'argTable[0]')
tkk7m.c:60: warning: data definition has no type or storage class
tkk7m.c:125: error: syntax error before 'a'
tkk7m.c: In function 'observation':
tkk7m.c:139: error: 'interp' undeclared (first use in this function)
tkk7m.c:139: error: (Each undeclared identifier is reported only once
tkk7m.c:139: error: for each function it appears in.)
tkk7m.c:139: error: 'TCL_OK' undeclared (first use in this function)
tkk7m.c:139: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:139: error: 'stderr' undeclared (first use in this function)
tkk7m.c:155: warning: incompatible implicit declaration of built-in function 'sprintf'
tkk7m.c:156: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:158: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:160: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:162: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:167: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:169: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:177: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:200: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:213: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:216: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:237: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c: At top level:
tkk7m.c:245: error: syntax error before 'a'
tkk7m.c: In function 'setclock':
tkk7m.c:251: error: 'argv' undeclared (first use in this function)
tkk7m.c:251: error: 'argc' undeclared (first use in this function)
tkk7m.c:263: warning: incompatible implicit declaration of built-in function 'sprintf'
tkk7m.c:264: error: 'interp' undeclared (first use in this function)
tkk7m.c:264: error: 'TCL_OK' undeclared (first use in this function)
tkk7m.c:264: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:264: error: 'stderr' undeclared (first use in this function)
tkk7m.c: At top level:
tkk7m.c:269: error: syntax error before 'a'
tkk7m.c: In function 'auto_manual':
tkk7m.c:273: error: 'interp' undeclared (first use in this function)
tkk7m.c:273: error: 'TCL_OK' undeclared (first use in this function)
tkk7m.c:273: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:273: error: 'stderr' undeclared (first use in this function)
tkk7m.c:277: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c: In function 'DisplayConfFile':
tkk7m.c:295: warning: incompatible implicit declaration of built-in function 'sprintf'
tkk7m.c:295: error: missing terminating " character
tkk7m.c:296: error: 'wm' undeclared (first use in this function)
tkk7m.c:296: error: syntax error before 'title'
tkk7m.c:296: error: stray '\' in program
tkk7m.c:296: error: missing terminating " character
tkk7m.c:297: error: stray '\' in program
tkk7m.c:297: error: missing terminating " character
tkk7m.c: At top level:
tkk7m.c:311: error: stray '\' in program
tkk7m.c:311: error: missing terminating " character
tkk7m.c:312: error: stray '\' in program
tkk7m.c:312: error: missing terminating " character
tkk7m.c:316: error: stray '\' in program
tkk7m.c:316: error: missing terminating " character
tkk7m.c:318: error: stray '\' in program
tkk7m.c:318: error: missing terminating " character
tkk7m.c:319: error: stray '\' in program
tkk7m.c:319: error: missing terminating " character
tkk7m.c:325: error: stray '\' in program
tkk7m.c:325: error: missing terminating " character
tkk7m.c:326: error: stray '\' in program
tkk7m.c:326: error: missing terminating " character
tkk7m.c:330: error: stray '\' in program
tkk7m.c:330: error: missing terminating " character
tkk7m.c:335: error: stray '\' in program
tkk7m.c:335: error: missing terminating " character
tkk7m.c:337: error: stray '\' in program
tkk7m.c:337: error: missing terminating " character
tkk7m.c:342: error: missing terminating " character
tkk7m.c:379: error: syntax error before '*' token
tkk7m.c: In function 'MyAppInit':
tkk7m.c:388: error: 'interp' undeclared (first use in this function)
tkk7m.c:388: error: 'TCL_OK' undeclared (first use in this function)
tkk7m.c:388: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:388: error: 'stderr' undeclared (first use in this function)
tkk7m.c:391: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:392: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:395: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:397: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:399: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:403: warning: incompatible implicit declaration of built-in function 'fprintf'
tkk7m.c:409: warning: incompatible implicit declaration of built-in function 'fprintf'
make[1]: *** [tkk7m.o] Error 1
make[1]: Leaving directory `/home/marco/Desktop/k7mctrl-0.2a/tk'
make: *** [all] Error 2
marco@server:~/Desktop/k7mctrl-0.2a$

```

---

