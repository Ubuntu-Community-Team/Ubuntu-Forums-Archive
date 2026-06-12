---
title: "error message when typing &quot;make&quot;"
date: 2006-04-01
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-04-01
Hey, I'm trying to install some audio codec, according to how it is described at the thread [k3b and monkeyaudio ape format]("http://ubuntuforums.org/showthread.php?t=119723&highlight=ape"). 
The same way is described in the package's INSTALL file.

But when typing "make", I get the following error message:
```
gabriel@ubuntu:~/k3bmonkeyaudioplugin-3.0/po$ make
make: *** No targets specified and no makefile found.  Stop.
```

How come? Why's the file missing?

G

---

### Post by KansasJoe on 2006-04-01
when you did the ./configure did it tell you if anything was missing?

---

### Post by GabrielWolff on 2006-04-01
[QUOTE=KansasJoe]when you did the ./configure did it tell you if anything was missing?[/QUOTE]
The last line is: ```
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

```
Whatwhat?
G

---

### Post by Sutekh on 2006-04-01
Try installing the development files for KDE
```
sudo apt-get install kdelibs4-dev
```
Annoying, but I believe neccessary to compile an application like k3b

---

### Post by Sef on 2006-04-01
Did you download build-essential?  If not, you can't compile.

sudo apt-get update

sudo apt-get install build-essential

---

### Post by GabrielWolff on 2006-04-01
I have done both, plus corrected a couple of other errors that appeared. The ./configure goes smooth now, appearantly.
Next error is the following: 
```
gabriel@ubuntu:~/k3bmonkeyaudioplugin-3.0$ make
make  all-recursive
make[1]: Entering directory `/home/gabriel/k3bmonkeyaudioplugin-3.0'
Making all in po
make[2]: Entering directory `/home/gabriel/k3bmonkeyaudioplugin-3.0/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/gabriel/k3bmonkeyaudioplugin-3.0/po'
Making all in src
make[2]: Entering directory `/home/gabriel/k3bmonkeyaudioplugin-3.0/src'
Making all in libmonkeyaudio
make[3]: Entering directory `/home/gabriel/k3bmonkeyaudioplugin-3.0/src/libmonkeyaudio'
Making all in Assembly
make[4]: Entering directory `/home/gabriel/k3bmonkeyaudioplugin-3.0/src/libmonkeyaudio/Assembly'
/bin/sh ../../../libtool --silent --mode=compile --tag=ASM sh ../../../strip_fPIC.sh  -f elf -d OBJ_FORMAT_elf Assembly.nas -o Assembly.lo
libtool: ignoring unknown tag ASM
-f elf -d OBJ_FORMAT_elf Assembly.nas -o .libs/Assembly.o
../../../strip_fPIC.sh: line 15: exec: -f: invalid option
exec: usage: exec [-cl] [-a name] file [redirection ...]
make[4]: *** [Assembly.lo] Error 1
make[4]: Leaving directory `/home/gabriel/k3bmonkeyaudioplugin-3.0/src/libmonkeyaudio/Assembly'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/gabriel/k3bmonkeyaudioplugin-3.0/src/libmonkeyaudio'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/gabriel/k3bmonkeyaudioplugin-3.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gabriel/k3bmonkeyaudioplugin-3.0'
make: *** [all] Error 2
gabriel@ubuntu:~/k3bmonkeyaudioplugin-3.0$

```

It's a bit too many character for me.

What's Error 2?

G

---

