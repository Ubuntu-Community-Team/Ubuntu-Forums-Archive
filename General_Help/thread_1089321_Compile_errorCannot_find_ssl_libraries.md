---
title: "Compile error:Cannot find ssl libraries"
date: 2009-03-07
forum: General Help
---

### Post by System Monitor on 2009-03-07
this is what i get when i try to compile

```
sam@ubuntu:~/Desktop/ophcrack-3.1.0$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... yes
checking for ranlib... ranlib
checking for Mac OS X or WIN32 or Solaris... no
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking whether byte ordering is bigendian... no
checking for libpthread... checking for pthread_mutex_init in -lpthread... yes
checking for libssl... configure: error: Cannot find ssl libraries

```

---

### Post by adult swim on 2009-03-07
run these
```
cd

sudo apt-get install libssl-dev

cd ~/Desktop/ophcrack-3.1.0

./configure
```

---

### Post by sdennie on 2009-03-07
It may have more libraries that you will need as well.  As this program already exists in the repos, you can use the following to get everything that was used to build the repo version of the software:

```

sudo apt-get build-dep ophcrack

```

---

### Post by leopardsaga on 2012-03-28
old topic.
Thanks for reminding the repo.

---

### Post by howefield on 2012-03-28
Old Thread closed.

---

