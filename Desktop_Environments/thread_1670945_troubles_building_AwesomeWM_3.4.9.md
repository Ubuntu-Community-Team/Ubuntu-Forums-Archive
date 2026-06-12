---
title: "troubles building AwesomeWM 3.4.9"
date: 2011-01-19
forum: Desktop Environments
---

### Post by 0nelove on 2011-01-19
Anybody having success building awesomeWM?  I've been using it for a few weeks from the .deb, but building the 3.4.9 (stable) is giving me some trouble.  Did have a go at installing the required dependencies as described in the wiki linked below, but still obviously missing something.  Thanks for any help.

```
Running make Makefile…
Building…
Scanning dependencies of target generated_sources
[  0%] Generating atoms-intern.h
[  0%] Generating atoms-extern.h
[  0%] Generating common/tokenize.c
[  0%] Generating common/tokenize.h
[  3%] Built target generated_sources
Scanning dependencies of target awesome
[  3%] Building C object CMakeFiles/awesome.dir/awesome.c.o
[  4%] Building C object CMakeFiles/awesome.dir/client.c.o
[  5%] Building C object CMakeFiles/awesome.dir/strut.c.o
[  6%] Building C object CMakeFiles/awesome.dir/dbus.c.o
[  6%] Building C object CMakeFiles/awesome.dir/root.c.o
[  7%] Building C object CMakeFiles/awesome.dir/event.c.o
/home/xx/awesome-3.4.9/event.c: In function ‘xerror’:
/home/xx/awesome-3.4.9/event.c:798: error: ‘XCB_EVENT_ERROR_BAD_WINDOW’ undeclared (first use in this function)
/home/xx/awesome-3.4.9/event.c:798: error: (Each undeclared identifier is reported only once
/home/xx/awesome-3.4.9/event.c:798: error: for each function it appears in.)
/home/xx/awesome-3.4.9/event.c:799: error: ‘XCB_EVENT_ERROR_BAD_MATCH’ undeclared (first use in this function)
/home/xx/awesome-3.4.9/event.c:801: error: ‘XCB_EVENT_ERROR_BAD_VALUE’ undeclared (first use in this function)
make[3]: *** [CMakeFiles/awesome.dir/event.c.o] Error 1
make[2]: *** [CMakeFiles/awesome.dir/all] Error 2
make[1]: *** [all] Error 2
make: *** [cmake-build] Error 2


```
similar problem here: [http://superuser.com/questions/232495/building-awesome-wm](http://superuser.com/questions/232495/building-awesome-wm)
similar error, unresolved:
[http://askubuntu.com/questions/21281/building-awesome-wm](http://askubuntu.com/questions/21281/building-awesome-wm)
build instructions (old): [https://awesome.naquadah.org/wiki/Awesome-3-Ubuntu-git](https://awesome.naquadah.org/wiki/Awesome-3-Ubuntu-git)

...

multiple duplicate posts below - whoops.  sry mods.  pls delete other 4:
[http://ubuntuforums.org/showthread.php?t=1670920](http://ubuntuforums.org/showthread.php?t=1670920)
[http://ubuntuforums.org/showthread.php?t=1670929](http://ubuntuforums.org/showthread.php?t=1670929)
[http://ubuntuforums.org/showthread.php?t=1670930](http://ubuntuforums.org/showthread.php?t=1670930)
[http://ubuntuforums.org/showthread.php?t=1670932](http://ubuntuforums.org/showthread.php?t=1670932)

---

