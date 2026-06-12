---
title: "Help with installing GTK+ in Ubuntu 8.10"
date: 2009-04-16
forum: General Help
---

### Post by Samual on 2009-04-16
Hi everyone, a few months ago I switched from Windows to Linux on my main desktop for full time use. I'm a programmer, so I need to be able to program and compile applications on Linux. I have decided I wanted to use GTK+ for my windows (Since it is cross platform), and i'm having trouble installing (configuring actually) because of this reason:

GTK+ requires many dependencies, including but not limited to glib, atk, cairo, pango... I installed Glib-2.19.10 which satisfied that dependancy, but unfortunately I can't install atk cairo or pango without installing an EARLIER version of glib. Which means I get one of two errors while running ./configure:

**_#1 (Missing Pango and ATK, yet glib is satisfied):_**
```

checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.19.7    atk >= 1.13.0    pango >= 1.20    cairo >= 1.6) were not met:

No package 'atk' found
No package 'pango' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

sam@DIOTECKTEC-Ubu:~/gtk+-2.16.0$ 

```


**_#2 (I have glib-2.19.10 installed, but it sees an earlier version):_**
```

checking for GLIB - version >= 2.19.7... 
*** 'pkg-config --modversion glib-2.0' returned 2.19.10, but GLIB (2.18.2)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.19.7 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/pub/gtk/.
sam@DIOTECKTEC-Ubu:~/gtk+-2.16.0$ 

```

Now, I need SOMEHOW to get both of these situations satisfied... if i'm doing something wrong here, please tell me.

I'm trying to install the latest stable GTK+ package, as well as the latest stable GLIB package.

If anyone has any ideas, I'll be very happy. :D


**_Full ./configure output:_**
```

sam@DIOTECKTEC-Ubu:~/gtk+-2.16.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for native Win32... no
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
checking for c++... c++
checking whether we are using the GNU C++ compiler... yes
checking whether c++ accepts -g... yes
checking dependency style of c++... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether c++ accepts -g... (cached) yes
checking dependency style of c++... (cached) gcc3
checking how to run the C++ preprocessor... c++ -E
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for ld used by c++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the c++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for c++ option to produce PIC... -fPIC -DPIC
checking if c++ PIC flag -fPIC -DPIC works... yes
checking if c++ static flag -static works... yes
checking if c++ supports -c -o file.o... yes
checking if c++ supports -c -o file.o... (cached) yes
checking whether the c++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
configure: creating ./config.lt
config.lt: creating libtool
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking for nm... /usr/bin/nm -B
checking whether to enable maintainer-specific portions of Makefiles... no
checking for some Win32 platform... no
checking whether build environment is sane... yes
checking for library containing strerror... none required
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... yes
checking Whether to write dependencies into .pc files... no
checking for perl5... no
checking for perl... /usr/bin/perl
checking for indent... no
checking for lstat... yes
checking for mkstemp... yes
checking for flockfile... yes
checking for getc_unlocked... yes
checking for localtime_r... yes
checking for _NL_TIME_FIRST_WEEKDAY... yes
checking for _NL_MEASUREMENT_MEASUREMENT... yes
checking for _NL_PAPER_HEIGHT... yes
checking for _NL_PAPER_WIDTH... yes
checking for sigsetjmp... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  af am ang ar as ast az az_IR be be@latin bg bn bn_IN br bs ca ca@valencia crh cs cy da de dz el en_CA en_GB eo es et eu fa fi fr ga gl gu he hi hr hu hy ia id io is it ja ka kn ko ku li lt lv mai mi mk ml mn mr ms nb ne nl nn nso oc or pa pl ps pt pt_BR ro ru rw si sk sl sq sr sr@latin sr@ije sv ta te th tk tr tt uk ur uz uz@cyrillic vi wa xh yi zh_CN zh_HK zh_TW
checking for extra flags to get ANSI library prototypes... none needed
checking for the BeOS... no
checking for HP-UX... no
checking for extra flags for POSIX compliance... none needed
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.19.7... 
*** 'pkg-config --modversion glib-2.0' returned 2.19.10, but GLIB (2.18.2)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.19.7 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/pub/gtk/.

```

Thanks again, Samual.

---

### Post by Samual on 2009-04-16
I happily figured this out with help from the #ubuntu channel on FreeNode. - Turns out I didn't need to compile GTK+, I simply needed to install libgtk2.0-dev, and then use a certain syntax while attempting to compile.

---

### Post by michaelwigle on 2009-05-07
What was the syntax that worked for you? I was able to get GTK+ to compile after a couple weeks of messing around but it broke quite a few other things in the process. I'm running 9.04 now and don't want to run into the same problem again.

---

### Post by Samual on 2009-05-08
> **michaelwigle said:**
> What was the syntax that worked for you? I was able to get GTK+ to compile after a couple weeks of messing around but it broke quite a few other things in the process. I'm running 9.04 now and don't want to run into the same problem again.

gcc $(pkg-config --cflags --libs gtk+-2.0) -o <name> <.c file>

Hope it works!

-- Should work in 9.04, haven't tried it in 9.04. Just make sure you have the GTK+ dev libs installed (They should be)

---

