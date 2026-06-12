---
title: "Installing from Source"
date: 2006-02-25
forum: Desktop Environments
---

### Post by subski on 2006-02-25
I was installing Scilab 4.0 from source.
After ./configure.
I tried 
     make all
i got command not found
any ideas?

---

### Post by bluevoodoo1 on 2006-02-25
Is there a readme file? Is the second command (after ./configure) "make" or "make all" or some thing else? Do you have the build-essential package?

sudo apt-get install build-essential

---

### Post by Ramses de Norre on 2006-02-25
I'm also having trouble with this package, the read me says to run ./configure and the make all. But make all gives me ```
ramses@icarus:~/.scilab-4.0$ make all
make: *** No rule to make target `all'.  Stop.

```
What could be wrong? I've got build essential installed, also gcc and g77 like the read me says. I've had this error with other packages before.

---

### Post by taurus on 2006-02-25
Have you tried

sudo make install

---

### Post by Ramses de Norre on 2006-02-25
That gives quiet the same error..
```
ramses@icarus:~/.scilab-4.0$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.

```

---

### Post by taurus on 2006-02-25
I am sure most programs require you to do

./configure
make
sudo make install

Do you see a message saying something like generting Makefiles at the end of ./configure?

---

### Post by Perfect Storm on 2006-02-25
When you compile you have to check the outcome of when you run ./configure it also tells you what is missing, which libs it's depended upon etc.

I've just tested it.

What you need is besides the basics compile tool which someone described before you need to install 

```
sudo apt-get install g77 x-window-system-dev tcl8.4-dev
./configure <you might add some flags to optimize it>
```

Afterwards

```
make all
```

For more information there's a Readme_Unix in the folder.

---

### Post by Ramses de Norre on 2006-02-28
I'm still getting the same errors..
```
ramses@icarus:~/.scilab-4.0$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
configuration of libtool
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... g77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether g77 accepts -g... yes
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
end of configuration of libtool
checking for main in -lieee... yes
checking for g77... yes
checking for X... libraries /usr/X11R6/lib, headers
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for X11 release... R6
checking for main in -lXmu... yes
checking for main in -lXaw3d... no
checking for javac... no
configure: WARNING: javac not found: I will not build the java interface
checking for leading and/or trailing underscores... no yes
checking for use of sharpsign in CPP... yes
checking for main in -lm... yes
checking for exp10... yes
checking for getwd... yes
checking for sleep... yes
checking for strerror... yes
checking for usleep... yes
checking for finite... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking values.h usability... yes
checking values.h presence... yes
checking for values.h... yes
checking for main in -lncurses... no
checking for main in -lcurses... no
checking for main in -ltermcap... no
checking for main in -ltermlib... no
checking for PVM architecture... LINUX
checking for main in -ldl... yes
checking for header file tcl.h... found in /usr/include/tcl8.4
checking if tcl is version 8.4 or later... (8.4) yes
checking for tcl library tcl8.4... found /usr/lib/libtcl8.4.so using -L/usr/lib -ltcl8.4
checking for Tcl_DoOneEvent in -ltcl8.4... yes
checking for header file tk.h... configure: error: header file tk.h  has been found for 8.4*  but no corresponding tk library
ramses@icarus:~/.scilab-4.0$ make all
make: *** No rule to make target `all'.  Stop.
ramses@icarus:~/.scilab-4.0$ sudo make all
make: *** No rule to make target `all'.  Stop.
ramses@icarus:~/.scilab-4.0$
```
This is what my ./configure output looks like and the error message on make all.
I don't know how to troubleshoot this..:-?

---

### Post by Remmelas on 2006-02-28
```
checking for header file tk.h... configure: error: header file tk.h  has been found for 8.4*  but no corresponding tk library
```

looks like u are missing a library.  Until configure completes with out errors, you won't be able to use 'make' at all.  based on this, u prolly need to ```
sudo apt-get install tk8.4-dev
```

---

### Post by Ramses de Norre on 2006-02-28
Ok, guess I missed that one. Now the make all command works.
But I'm having a new error: ```
 -------- Creation of util (Macros) --------
 !--error 9999
Impossible to open file ...mses/.binlab-4.0/macros/util/gettklib.bin for writingat line      27 of function getsave called by :
line    87 of function genlib called by :
genlib('utillib','SCI/macros/util');
line  -258 of exec file called by :
  exec('buildmacros.sce');
line    37 of exec file called by :
exec('buildmacros.sce',-1)


-->

```
This shows up after a while..

Why is it so hard to compile a program? I have no clue what to do next..

---

### Post by Remmelas on 2006-02-28
once your build environment is used a few times you'll run into less problems, cuz you'll have more dependencies installed, and practice so don't get discouraged.

The last error i'm not sure about, but it may be trying to use a file that your normal user doesn't have permissions to, or doesn't exist.  It's normally not good practice to run make as root, but sometimes it's necessary.  You could try executing make with sudo and see if the error clears.

---

