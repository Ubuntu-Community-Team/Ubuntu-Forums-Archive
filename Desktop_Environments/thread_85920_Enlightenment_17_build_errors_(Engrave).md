---
title: "Enlightenment 17 build errors (Engrave)"
date: 2005-11-03
forum: Desktop Environments
---

### Post by not_cool on 2005-11-03
I am trying to compile the E17 CVS code because I don't want E16.7. I have followed the directions at [http://http://www.get-e.org/User_Guide/English/_pages/2.1.html]("http://http://www.get-e.org/User_Guide/English/_pages/2.1.html") and have installed all of the modules up to ewl. I didn't install etox though. (It says you don't need to.) When I try to install engrave I get an error message saying I need to install automake-1.5: 

```
markus@ubuntu:~$ cd e17
markus@ubuntu:~/e17$ cd libs
markus@ubuntu:~/e17/libs$ cd engrave
markus@ubuntu:~/e17/libs/engrave$ ./autogen.sh
Running aclocal...
Running autoheader...
configure.in:17: warning: AC_PROG_LEX invoked multiple times
autoconf/programs.m4:438: AC_DECL_YYTEXT is expanded from...
aclocal.m4:7013: AM_PROG_LEX is expanded from...
configure.in:17: the top level
Running autoconf...
configure.in:17: warning: AC_PROG_LEX invoked multiple times
autoconf/programs.m4:438: AC_DECL_YYTEXT is expanded from...
aclocal.m4:7013: AM_PROG_LEX is expanded from...
configure.in:17: the top level
Running libtoolize...
Running automake...
Makefile.am:2: require version 1.5, but have 1.4-p6
src/bin/Makefile.am:1: require version 1.5, but have 1.4-p6
markus@ubuntu:~/e17/libs/engrave$

```

I try to install the automake-1.5 source and get this error message when running
```
markus@ubuntu:~/e17/libs/<module>$./autogen.sh
```

Error:

```
markus@ubuntu:~/e17/libs/engrave$ ./autogen.sh
Running aclocal...
aclocal: configure.in: 15: macro `AM_ENABLE_SHARED' not found in library
aclocal: configure.in: 16: macro `AM_PROG_LIBTOOL' not found in library
```

This is the process I used to install automake-1.5:

```
markus@ubuntu:~$ cd automake-1.5
markus@ubuntu:~/automake-1.5$ ./configure
loading cache ./config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking for mawk... (cached) mawk
checking whether make sets ${MAKE}... (cached) yes
checking for perl... (cached) /usr/bin/perl
creating ./config.status
creating Makefile
creating lib/Makefile
creating lib/Automake/Makefile
creating lib/am/Makefile
creating m4/Makefile
creating tests/Makefile
creating automake
creating aclocal
markus@ubuntu:~/automake-1.5$ make
Making all in .
make[1]: Entering directory `/home/markus/automake-1.5'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/markus/automake-1.5'
Making all in m4
make[1]: Entering directory `/home/markus/automake-1.5/m4'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/markus/automake-1.5/m4'
Making all in lib
make[1]: Entering directory `/home/markus/automake-1.5/lib'
Making all in Automake
make[2]: Entering directory `/home/markus/automake-1.5/lib/Automake'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/markus/automake-1.5/lib/Automake'
Making all in am
make[2]: Entering directory `/home/markus/automake-1.5/lib/am'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/markus/automake-1.5/lib/am'
make[2]: Entering directory `/home/markus/automake-1.5/lib'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/markus/automake-1.5/lib'
make[1]: Leaving directory `/home/markus/automake-1.5/lib'
Making all in tests
make[1]: Entering directory `/home/markus/automake-1.5/tests'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/markus/automake-1.5/tests'
markus@ubuntu:~/automake-1.5$ sudo make install
Password:
Making install in .
make[1]: Entering directory `/home/markus/automake-1.5'
make[2]: Entering directory `/home/markus/automake-1.5'
/bin/sh ./lib/mkinstalldirs /usr/local/bin
 /usr/bin/install -c automake /usr/local/bin/automake
 /usr/bin/install -c aclocal /usr/local/bin/aclocal
/bin/sh ./lib/mkinstalldirs /usr/local/info
 /usr/bin/install -c -m 644 ./automake.info /usr/local/info/automake.info
 /usr/bin/install -c -m 644 ./automake.info-1 /usr/local/info/automake.info-1
 /usr/bin/install -c -m 644 ./automake.info-2 /usr/local/info/automake.info-2
 /usr/bin/install -c -m 644 ./automake.info-3 /usr/local/info/automake.info-3
 /usr/bin/install -c -m 644 ./automake.info-4 /usr/local/info/automake.info-4
 install-info --info-dir=/usr/local/info /usr/local/info/automake.info
* automake: (automake). Making Makefile.in's
make[2]: Leaving directory `/home/markus/automake-1.5'
make[1]: Leaving directory `/home/markus/automake-1.5'
Making install in m4
make[1]: Entering directory `/home/markus/automake-1.5/m4'
make[2]: Entering directory `/home/markus/automake-1.5/m4'
make[2]: Nothing to be done for `install-exec-am'.
/bin/sh ../lib/mkinstalldirs /usr/local/share/aclocal
 /usr/bin/install -c -m 644 as.m4 /usr/local/share/aclocal/as.m4
 /usr/bin/install -c -m 644 auxdir.m4 /usr/local/share/aclocal/auxdir.m4
 /usr/bin/install -c -m 644 ccstdc.m4 /usr/local/share/aclocal/ccstdc.m4
 /usr/bin/install -c -m 644 cond.m4 /usr/local/share/aclocal/cond.m4
 /usr/bin/install -c -m 644 depend.m4 /usr/local/share/aclocal/depend.m4
 /usr/bin/install -c -m 644 depout.m4 /usr/local/share/aclocal/depout.m4
 /usr/bin/install -c -m 644 dmalloc.m4 /usr/local/share/aclocal/dmalloc.m4
 /usr/bin/install -c -m 644 error.m4 /usr/local/share/aclocal/error.m4
 /usr/bin/install -c -m 644 gcj.m4 /usr/local/share/aclocal/gcj.m4
 /usr/bin/install -c -m 644 header.m4 /usr/local/share/aclocal/header.m4
 /usr/bin/install -c -m 644 init.m4 /usr/local/share/aclocal/init.m4
 /usr/bin/install -c -m 644 install-sh.m4 /usr/local/share/aclocal/install-sh.m4
 /usr/bin/install -c -m 644 lex.m4 /usr/local/share/aclocal/lex.m4
 /usr/bin/install -c -m 644 lispdir.m4 /usr/local/share/aclocal/lispdir.m4
 /usr/bin/install -c -m 644 make.m4 /usr/local/share/aclocal/make.m4
 /usr/bin/install -c -m 644 maintainer.m4 /usr/local/share/aclocal/maintainer.m4
 /usr/bin/install -c -m 644 minuso.m4 /usr/local/share/aclocal/minuso.m4
 /usr/bin/install -c -m 644 missing.m4 /usr/local/share/aclocal/missing.m4
 /usr/bin/install -c -m 644 multi.m4 /usr/local/share/aclocal/multi.m4
 /usr/bin/install -c -m 644 obstack.m4 /usr/local/share/aclocal/obstack.m4
 /usr/bin/install -c -m 644 protos.m4 /usr/local/share/aclocal/protos.m4
 /usr/bin/install -c -m 644 ptrdiff.m4 /usr/local/share/aclocal/ptrdiff.m4
 /usr/bin/install -c -m 644 python.m4 /usr/local/share/aclocal/python.m4
 /usr/bin/install -c -m 644 regex.m4 /usr/local/share/aclocal/regex.m4
 /usr/bin/install -c -m 644 sanity.m4 /usr/local/share/aclocal/sanity.m4
 /usr/bin/install -c -m 644 strip.m4 /usr/local/share/aclocal/strip.m4
 /usr/bin/install -c -m 644 strtod.m4 /usr/local/share/aclocal/strtod.m4
 /usr/bin/install -c -m 644 termios.m4 /usr/local/share/aclocal/termios.m4
 /usr/bin/install -c -m 644 winsz.m4 /usr/local/share/aclocal/winsz.m4
make[2]: Leaving directory `/home/markus/automake-1.5/m4'
make[1]: Leaving directory `/home/markus/automake-1.5/m4'
Making install in lib
make[1]: Entering directory `/home/markus/automake-1.5/lib'
Making install in Automake
make[2]: Entering directory `/home/markus/automake-1.5/lib/Automake'
make[3]: Entering directory `/home/markus/automake-1.5/lib/Automake'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../../lib/mkinstalldirs /usr/local/share/automake/Automake
 /usr/bin/install -c -m 644 Struct.pm /usr/local/share/automake/Automake/Struct.pm
make[3]: Leaving directory `/home/markus/automake-1.5/lib/Automake'
make[2]: Leaving directory `/home/markus/automake-1.5/lib/Automake'
Making install in am
make[2]: Entering directory `/home/markus/automake-1.5/lib/am'
make[3]: Entering directory `/home/markus/automake-1.5/lib/am'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../../lib/mkinstalldirs /usr/local/share/automake/am
 /usr/bin/install -c -m 644 ansi2knr.am /usr/local/share/automake/am/ansi2knr.am
 /usr/bin/install -c -m 644 check.am /usr/local/share/automake/am/check.am
 /usr/bin/install -c -m 644 clean-hdr.am /usr/local/share/automake/am/clean-hdr.am
 /usr/bin/install -c -m 644 clean.am /usr/local/share/automake/am/clean.am
 /usr/bin/install -c -m 644 compile.am /usr/local/share/automake/am/compile.am
 /usr/bin/install -c -m 644 configure.am /usr/local/share/automake/am/configure.am
 /usr/bin/install -c -m 644 data.am /usr/local/share/automake/am/data.am
 /usr/bin/install -c -m 644 dejagnu.am /usr/local/share/automake/am/dejagnu.am
 /usr/bin/install -c -m 644 depend.am /usr/local/share/automake/am/depend.am
 /usr/bin/install -c -m 644 depend2.am /usr/local/share/automake/am/depend2.am
 /usr/bin/install -c -m 644 distdir.am /usr/local/share/automake/am/distdir.am
 /usr/bin/install -c -m 644 footer.am /usr/local/share/automake/am/footer.am
 /usr/bin/install -c -m 644 header-vars.am /usr/local/share/automake/am/header-vars.am
 /usr/bin/install -c -m 644 header.am /usr/local/share/automake/am/header.am
 /usr/bin/install -c -m 644 install.am /usr/local/share/automake/am/install.am
 /usr/bin/install -c -m 644 java.am /usr/local/share/automake/am/java.am
 /usr/bin/install -c -m 644 lang-compile.am /usr/local/share/automake/am/lang-compile.am
 /usr/bin/install -c -m 644 lex.am /usr/local/share/automake/am/lex.am
 /usr/bin/install -c -m 644 library.am /usr/local/share/automake/am/library.am
 /usr/bin/install -c -m 644 libs.am /usr/local/share/automake/am/libs.am
 /usr/bin/install -c -m 644 libtool.am /usr/local/share/automake/am/libtool.am
 /usr/bin/install -c -m 644 lisp.am /usr/local/share/automake/am/lisp.am
 /usr/bin/install -c -m 644 ltlib.am /usr/local/share/automake/am/ltlib.am
 /usr/bin/install -c -m 644 ltlibrary.am /usr/local/share/automake/am/ltlibrary.am
 /usr/bin/install -c -m 644 mans-vars.am /usr/local/share/automake/am/mans-vars.am
 /usr/bin/install -c -m 644 mans.am /usr/local/share/automake/am/mans.am
 /usr/bin/install -c -m 644 multilib.am /usr/local/share/automake/am/multilib.am
 /usr/bin/install -c -m 644 program.am /usr/local/share/automake/am/program.am
 /usr/bin/install -c -m 644 progs.am /usr/local/share/automake/am/progs.am
 /usr/bin/install -c -m 644 python.am /usr/local/share/automake/am/python.am
 /usr/bin/install -c -m 644 remake-hdr.am /usr/local/share/automake/am/remake-hdr.am
 /usr/bin/install -c -m 644 scripts.am /usr/local/share/automake/am/scripts.am
 /usr/bin/install -c -m 644 subdirs.am /usr/local/share/automake/am/subdirs.am
 /usr/bin/install -c -m 644 tags.am /usr/local/share/automake/am/tags.am
 /usr/bin/install -c -m 644 texi-vers.am /usr/local/share/automake/am/texi-vers.am
 /usr/bin/install -c -m 644 texibuild.am /usr/local/share/automake/am/texibuild.am
 /usr/bin/install -c -m 644 texinfos.am /usr/local/share/automake/am/texinfos.am
 /usr/bin/install -c -m 644 yacc.am /usr/local/share/automake/am/yacc.am
make[3]: Leaving directory `/home/markus/automake-1.5/lib/am'
make[2]: Leaving directory `/home/markus/automake-1.5/lib/am'
make[2]: Entering directory `/home/markus/automake-1.5/lib'
make[3]: Entering directory `/home/markus/automake-1.5/lib'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../lib/mkinstalldirs /usr/local/share/automake
 /usr/bin/install -c -m 644 COPYING /usr/local/share/automake/COPYING
 /usr/bin/install -c -m 644 INSTALL /usr/local/share/automake/INSTALL
 /usr/bin/install -c -m 644 texinfo.tex /usr/local/share/automake/texinfo.tex
 /usr/bin/install -c -m 644 ansi2knr.c /usr/local/share/automake/ansi2knr.c
 /usr/bin/install -c -m 644 ansi2knr.1 /usr/local/share/automake/ansi2knr.1
/bin/sh ../lib/mkinstalldirs /usr/local/share/automake
 /usr/bin/install -c -m 644 config.guess /usr/local/share/automake/config.guess
 /usr/bin/install -c -m 644 config.sub /usr/local/share/automake/config.sub
 /usr/bin/install -c -m 644 install-sh /usr/local/share/automake/install-sh
 /usr/bin/install -c -m 644 mdate-sh /usr/local/share/automake/mdate-sh
 /usr/bin/install -c -m 644 missing /usr/local/share/automake/missing
 /usr/bin/install -c -m 644 mkinstalldirs /usr/local/share/automake/mkinstalldirs
 /usr/bin/install -c -m 644 elisp-comp /usr/local/share/automake/elisp-comp
 /usr/bin/install -c -m 644 ylwrap /usr/local/share/automake/ylwrap
 /usr/bin/install -c -m 644 acinstall /usr/local/share/automake/acinstall
 /usr/bin/install -c -m 644 depcomp /usr/local/share/automake/depcomp
 /usr/bin/install -c -m 644 compile /usr/local/share/automake/compile
 /usr/bin/install -c -m 644 py-compile /usr/local/share/automake/py-compile
make  install-data-hook
make[4]: Entering directory `/home/markus/automake-1.5/lib'
 chmod +x /usr/local/share/automake/config.guess
 chmod +x /usr/local/share/automake/config.sub
 chmod +x /usr/local/share/automake/install-sh
 chmod +x /usr/local/share/automake/mdate-sh
 chmod +x /usr/local/share/automake/missing
 chmod +x /usr/local/share/automake/mkinstalldirs
 chmod +x /usr/local/share/automake/elisp-comp
 chmod +x /usr/local/share/automake/ylwrap
 chmod +x /usr/local/share/automake/acinstall
 chmod +x /usr/local/share/automake/depcomp
 chmod +x /usr/local/share/automake/compile
 chmod +x /usr/local/share/automake/py-compile
make[4]: Leaving directory `/home/markus/automake-1.5/lib'
make[3]: Leaving directory `/home/markus/automake-1.5/lib'
make[2]: Leaving directory `/home/markus/automake-1.5/lib'
make[1]: Leaving directory `/home/markus/automake-1.5/lib'
Making install in tests
make[1]: Entering directory `/home/markus/automake-1.5/tests'
make[2]: Entering directory `/home/markus/automake-1.5/tests'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/markus/automake-1.5/tests'
make[1]: Leaving directory `/home/markus/automake-1.5/tests'
markus@ubuntu:~/automake-1.5$   
```

By the way my installation steps for the other modules are:

```
markus@ubuntu:~/e17/libs/<module>$./autogen.sh
markus@ubuntu:~/e17/libs/<module>$make #or sometimes sudo make
markus@ubuntu:~/e17/libs/<module>$sudo make install
markus@ubuntu:~/e17/libs/<module>$sudo ldconfig
```

---

### Post by Ampersand on 2005-11-03
I've found that this script works well for E17: [http://dev.winged.it/download/enlightened_stuff/enlightenment_updater_script](http://dev.winged.it/download/enlightened_stuff/enlightenment_updater_script).

If you install automake1.7 (available in Synaptic), it should all work (it did for me, anyway).

---

### Post by not_cool on 2005-11-03
First of all, I already had (from Synaptic) automake-1.4, 1.6, 1.7, 1.8, 1.9, but Engrave says that it needs automake-1.5 anyways. I downloaded the script and ran it but got the error:

```
=> Checking sudo access...
Password:
=> Checking /etc/ld.so.conf sanity...
| /etc/ld.so.conf paths don't contain e17 libs' path.               |
| Add /opt/e17/lib to /etc/ld.so.conf please.

```

Then I check to even see if there is such a directory as /opt/e17/lib

```
markus@ubuntu:/opt$ cd e17
bash: cd: e17: No such file or directory

```

Keep in mind that Enlightenent 17 isn't installed fully yet, I still have to install Engrave, which I get the errors for, and Emotion, which just needs to be installed.

---

### Post by not_cool on 2005-11-04
help!

---

