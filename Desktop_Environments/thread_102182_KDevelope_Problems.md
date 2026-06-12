---
title: "KDevelope Problems"
date: 2005-12-11
forum: Desktop Environments
---

### Post by Shadow-of-Evil on 2005-12-11
Everytime I try to build a project in KDevelope, even a hello world program, the output box says that KDevelope cannot find the command make.  Can anyone give me any suggestions?

Here is the output

cd '/home/shadowofevil/gcctest' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/shadowofevil/gcctest/debug' && cd '/home/shadowofevil/gcctest/debug' && CFLAGS="-O0 -g3 " "/home/shadowofevil/gcctest/configure" --enable-debug=full && cd '/home/shadowofevil/gcctest/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
/bin/sh: make: command not found
*** Exited with status: 127 ***

---

### Post by nrwilk on 2005-12-11
You need to install a program called "make" to be able to compile programs in kdevelop (or anywhere, really).

type this in a command prompt:
```
sudo apt-get update
sudo apt-get install make
```

---

### Post by kroiz on 2005-12-11
will he need also to apt-get g++?
or some other compiler?

---

### Post by nrwilk on 2005-12-11
Actually yes, but g++ is included with gcc.

so,
```
sudo apt-get install gcc
```

That will install gcc-4.0.

if you need gcc-3.4 for some reason (compiling nvidia drivers, or a kernel <= 2.6.12) do this:
```
sudo apt-get install gcc-3.4
```

you'll also need this if you haven't already gotten it:
```
sudo apt-get install build-essential
```

---

### Post by bbgun on 2006-01-12
Hello, I was having the same problems compiling C++ code with Kdevelop and typed in the commands that Fealos advised: 

sudo apt-get update
sudo apt-get install make


but when I tried to compile again I got a different error message:


*** YOU'RE USING automake (GNU automake) 1.4-p6.
*** KDE requires automake 1.6
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***

I tried to update automake but my system told me that 1.4 is the latest version... Can anyone help please?

---

### Post by Weman on 2006-01-14
Thank you Fealos, you solved my similar problems, compiles OK now.
// Weman

---

### Post by ganix on 2006-02-01
[QUOTE=bbgun]Hello, I was having the same problems compiling C++ code with Kdevelop and typed in the commands that Fealos advised: 

sudo apt-get update
sudo apt-get install make


but when I tried to compile again I got a different error message:


*** YOU'RE USING automake (GNU automake) 1.4-p6.
*** KDE requires automake 1.6
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***

I tried to update automake but my system told me that 1.4 is the latest version... Can anyone help please?[/QUOTE]
hi bbgun,
try installing the more recent version explicitly by ie.

sudo apt-get install autoconf1.9

maybe you have to remove the oder version, too

---

### Post by Lord Illidan on 2006-02-01
How about using synaptic, and installing all versions of automake. That is what I did.

Oh, and if it wants automake1.6, don't give it 1.9, it didn't work for me, at least. 1.6 must be installed, and that's that...

---

