---
title: "gtkEveMon installation?"
date: 2008-07-29
forum: Gaming &amp; Leisure
---

### Post by couzin2000 on 2008-07-29
I've got a VirtualBox running with [EveMon]("http://evemon.battleclinic.com/"), a small program to monitor Eve-Online character development. This takes up a lot of memory for nothing, and I would certainly like to run a program like that natively on Ubuntu, or even with Wine -- but EveMon **requires .Net 2.0**, so that can't be done.

Enter **gtkEveMon**, developed for Linux. Instructions are in the page to compile this program from source so that it runs directly on any Linux distro - but I am not sure, in this case, how to use the [FONT="Courier New"]make[/FONT] command. Can someone help?

Heres a link to the install instructions - they are particular to Gentoo, I think, but I need a "*Ubuntu translation*".
[_http://gtkevemon.battleclinic.com/download.html_]("http://gtkevemon.battleclinic.com/download.html")
Thanks!

---

### Post by Perfect Storm on 2008-07-29
Seems pretty simple enough (I don't use it though).

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential subversion
svn checkout svn://gtkevemon.battleclinic.com/GTKEVEMon/trunk/gtkevemon
cd gtkevemon
make
sudo make install
```

It properly complain about some libs -dev you need to install as well. Install those libs -dev and run the make command again until all dependencies are resolved.

---

### Post by localhorse on 2008-11-22
Did you get it working, couzin?

---

### Post by couzin2000 on 2009-02-12
yup - from the Battleclinic.com forums. Thx!

---

### Post by Vadi on 2009-02-12
getdeb.net is your friend: [http://www.getdeb.net/search.php?keywords=gtkevemon](http://www.getdeb.net/search.php?keywords=gtkevemon)

---

### Post by SubparUserdo on 2011-03-09
I'm glad couzin brought this up. I've been having the same problem, and the answer given by Artificial Intelligence worked great, right up until

```
$ make
```That brings up

```
make -C src
Package gtkmm-2.4 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkmm-2.4.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkmm-2.4' found
Package libxml-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml-2.0' found
make[1]: Entering directory `/home/david/gtkevemon/src'
g++ -c -o pipedexec_posix.o pipedexec_posix.cc -Wall -Wextra -ansi -Wundef -Wconversion -g -pedantic -O2  
Package gtkmm-2.4 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkmm-2.4.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkmm-2.4' found
Package libxml-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml-2.0' found
g++ -c -o os_unix.o os_unix.cc -Wall -Wextra -ansi -Wundef -Wconversion -g -pedantic -O2  
Package gtkmm-2.4 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkmm-2.4.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkmm-2.4' found
Package libxml-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml-2.0' found
g++ -c -o maingui.o maingui.cc -Wall -Wextra -ansi -Wundef -Wconversion -g -pedantic -O2  
maingui.cc:3: fatal error: gtkmm/button.h: No such file or directory
compilation terminated.
make[1]: *** [maingui.o] Error 1
make[1]: Leaving directory `/home/david/gtkevemon/src'
make: *** [all] Error 2

```

I've been reading, and it seems like I'm just missing some libraries. I'm not sure where to get them, if they're all part of the same package, or what. Is that right, or am I missing something else?

---

### Post by Perfect Storm on 2011-03-09
Install: 

libgtkmm-2.4-dev
libxml2-dev

Then run
**make clean**

then try again.

---

### Post by SubparUserdo on 2011-03-09
Ubuntuforums to the rescue again. Thank you!

---

