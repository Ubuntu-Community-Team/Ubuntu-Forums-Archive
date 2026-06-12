---
title: "[SOLVED] gimp 2.6 installed under the dpkg name &amp;quot;gimp,&amp;quot; ./configure wants &amp;quot;gimp-2.0&amp;quot; "
date: 2008-12-14
forum: General Help
---

### Post by MaxIBoy on 2008-12-14
Okay, I'm trying to install gimp-GAP. Gimp-GAP wants Gimp version 2.4 or later, I have 2.6. The package is called "gimp," as you can see here:
```
maxtothemax@maxtothemax-desktop:~$ dpkg -l gimp
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  gimp           2.6.1-1~getdeb The GNU Image Manipulation Program
maxtothemax@maxtothemax-desktop:~$ 

```


However, Gimp-GAP's compiling script wants the package to be named "gimp-2.0," as you can see here:
```
maxtothemax@maxtothemax-desktop:~/gimp-gap-2.4.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for ranlib... ranlib
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for unistd.h... (cached) yes
checking for bind_textdomain_codeset... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GIMP... configure: error: Package requirements (gimp-2.0 >= 2.4.0 gimpui-2.0 >= 2.4.0 gimpthumb-2.0 >= 2.4.0) were not met:

No package 'gimp-2.0' found
No package 'gimpui-2.0' found
No package 'gimpthumb-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GIMP_CFLAGS
and GIMP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

maxtothemax@maxtothemax-desktop:~/gimp-gap-2.4.0$ 

```



Is there any kind of aliasing I can do to get requests for "gimp-2.0" to be redirected to my "gimp" package? I don't want to install gimp all over again.

---

### Post by sedawk on 2008-12-14
Do you really need the latest version - it seems to be part
of ubuntu:
```

>aptitude search gap
...
p   gimp-gap                        - The GIMP Animation Package 
...

```

So on command line "sudo apt-get install gimp-gap" should do the trick.

At least that seems to be easier than to hack the "detection bug"
of ./configure.

---

### Post by kevdog on 2008-12-15
sudo aptitude install libgimp2.0-dev

you need the developmental files (not just the executables) installed.

---

### Post by MaxIBoy on 2008-12-15
> **sedawk said:**
> Do you really need the latest version - it seems to be part
of ubuntu:
```

>aptitude search gap
...
p   gimp-gap                        - The GIMP Animation Package 
...

```

So on command line "sudo apt-get install gimp-gap" should do the trick.

At least that seems to be easier than to hack the "detection bug"
of ./configure.



Ever have one of those moments when something seems "too obvious," so you don't try it? I'd installed gimp from getdeb, and gimp-gap wasn't in getdeb's repositories, so I assumed that the one from Ubuntu's repositories wouldn't work.

But it did. I expected to have an error message to show you, but it worked. Thank you.

---

### Post by huanix on 2011-01-27
> **kevdog said:**
> sudo aptitude install libgimp2.0-dev

you need the developmental files (not just the executables) installed.

Thank you so much. I spent 30 minutes trying to hack the config file to get gimp-deskew-plugin to compile - installing this package solved my problems!

---

