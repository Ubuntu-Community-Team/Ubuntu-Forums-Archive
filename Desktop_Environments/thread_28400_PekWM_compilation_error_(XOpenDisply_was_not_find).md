---
title: "PekWM compilation error (XOpenDisply was not find)"
date: 2005-04-20
forum: Desktop Environments
---

### Post by bashfreak on 2005-04-20
I am used to pekwm ([http://www.pekwm.org](http://www.pekwm.org)) but there is a problem during ./configure

# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for sed... sed
checking how to run the C++ preprocessor... g++ -E
checking for X... no
checking for XOpenDisplay in -lX11... no
configure: error: Could not find XOpenDisplay in -lX11.

'./configure --without-x' changes this only from 'checking for X... no' to 'checking for X... disabled'

checking for XOpenDisplay in -lX11... no
configure: error: Could not find XOpenDisplay in -lX11.
is still the same

I tried to install XFree libs, but it didn't help.


I have 5.04 updated every day with apt-get.

---

### Post by waft on 2005-06-09
i have the same problem. do I have to install anything? or is there any deb package?

---

### Post by alastair lewis on 2005-06-09
I came across a similar problem with lineakd. You probably need libx11-dev and libxt-dev.

Try ```
apt-get build-dep pekwm
``` This should sort out the missing dependancy issue. If not try the above libs. If you still stuck after that check the PekWM site for further help.

---

### Post by waft on 2005-06-13
thanks

---

### Post by oshi on 2005-07-09
I am having the same issue with PekWM

Fresh install, everything updated but when i try to compile pekwm i get:

```
oshi@wonderland:~/vm/pekwm-0.1.4pre2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for sed... sed
checking how to run the C++ preprocessor... g++ -E
checking for X... no
checking for XOpenDisplay in -lX11... no
configure: error: Could not find XOpenDisplay in -lX11.

``` 

any clues?

issue fixed with auto-apt
```
$ sudo apt-get install auto-apt
$ sudo auto-apt update
$ sudo auto-apt updatedb
$ sudo auto-apt update-local
$ auto-apt run ./configure
$ ./configure
```

---

