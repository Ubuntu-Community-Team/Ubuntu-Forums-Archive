---
title: "Error when building from source"
date: 2015-11-13
forum: Gaming &amp; Leisure
---

### Post by James_Guess on 2015-11-13
I recently tried building the launcher at [https://github.com/MCMrARM/mcpelauncher-linux](https://github.com/MCMrARM/mcpelauncher-linux)
and get the following error and don't know what I can/need to do to fix it
```
jamesguessis@senpai-chan:~/Downloads/mcpelauncher-linux-master$ make
Linking CXX executable mcpelauncher
CMakeFiles/mcpelauncher.dir/hybris/src/hooks.c.o: In function `my_pthread_attr_getstackaddr':
hooks.c:(.text+0x3f7): warning: the use of `pthread_attr_getstackaddr' is deprecated, use `pthread_attr_getstack'
CMakeFiles/mcpelauncher.dir/hybris/src/hooks.c.o: In function `my_pthread_attr_setstackaddr':
hooks.c:(.text+0x3d6): warning: the use of `pthread_attr_setstackaddr' is deprecated, use `pthread_attr_setstack'
/usr/bin/ld: cannot find -luuid
collect2: error: ld returned 1 exit status
CMakeFiles/mcpelauncher.dir/build.make:538: recipe for target 'mcpelauncher' failed
make[2]: *** [mcpelauncher] Error 1
CMakeFiles/Makefile2:60: recipe for target 'CMakeFiles/mcpelauncher.dir/all' failed
make[1]: *** [CMakeFiles/mcpelauncher.dir/all] Error 2
Makefile:75: recipe for target 'all' failed
make: *** [all] Error 2


```
What does this mean? And (if any) what are the fixes for it?

---

### Post by SeijiSensei on 2015-11-13
You can ignore the warnings.  The real problem is that "cannot find -luuid" error.  It's looking for a library you do not have installed. A quick search for that phrase on Google brings up a lot of postings.

On my pretty vanilla Kubuntu 14.04 machine, if I run "sudo apt-get install libuuid1" I'm told it's already installed.  You may need to install that, and you probably need to install uuid-dev, the package that contains the headers and other code required to compile and link to libuuid1.  So give this a try:
```
sudo apt-get install libuuid1 uuid-dev
```

If you're trying to build a package that already exists in the Ubuntu repositories, you can use the command
```
sudo apt-get build-dep package_name
```
like
```
sudo apt-get build-dep mplayer
```
The "build-dep" function downloads and installs any missing libraries and "-dev" code files.

If you're building a package that does not exist in the repositories, expect to spend some time tracking down and installing missing dependencies manually.

---

### Post by James_Guess on 2015-11-13
> **SeijiSensei said:**
>   So give this a try:
```
sudo apt-get install libuuid1 uuid-dev
```
> **SeijiSensei said:**
> If you're building a package that does not exist in the repositories, expect to spend some time tracking down and installing missing dependencies manually.
Yeah, I've tried with no luck, so I decided to turn to others :P
And Thank You for responding!

---

### Post by James_Guess on 2015-11-14
I figured it out.
needed the 32 bit package of uuid-dev

---

