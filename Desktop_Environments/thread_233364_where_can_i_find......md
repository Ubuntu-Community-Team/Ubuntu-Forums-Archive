---
title: "where can i find....."
date: 2006-08-10
forum: Desktop Environments
---

### Post by someguyouknow on 2006-08-10
the repositories with the latest k9copy?......
i have an older version that keeps crashing.....

or if you know of another k9copy/dvdshrink like app, i would like to know.....

thanks in advance:D

---

### Post by ciscosurfer on 2006-08-10
Search k9copy on the forums. Does [this help]("http://ubuntuforums.org/showthread.php?t=186273&highlight=k9copy")?  Maybe, [this]("http://www.google.com/search?hs=Mf2&hl=en&lr=&client=firefox&rls=Swiftfox%3Aen-US%3Aunofficial&q=k9copy+%2B+deb&btnG=Search")?

---

### Post by someguyouknow on 2006-08-10
i found the source but i cant seem to install it.....

this is what i get when i do make.....
```
make  all-recursive
make[1]: Entering directory `/home/someguyouknow/Progrums/k9copy-1.0.4-2/k9copy-1.0.4-2'
Making all in k9vamps
make[2]: Entering directory `/home/someguyouknow/Progrums/k9copy-1.0.4-2/k9copy-1.0.4-2/k9vamps'
source='k9vamps.cpp' object='k9vamps.lo' libtool=yes \
        depfile='.deps/k9vamps.Plo' tmpdepfile='.deps/k9vamps.TPlo' \
        depmode=gcc3 /bin/sh ../admin/depcomp \
        /bin/sh ../libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../libk9copy -I. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -c -o k9vamps.lo `test -f 'k9vamps.cpp' || echo './'`k9vamps.cpp
In file included from k9vamps.h:15,
                 from k9vamps.cpp:13:
../libk9copy/k9common.h:28:31: error: dvdread/ifo_types.h: No such file or directory
../libk9copy/k9common.h:29:32: error: dvdread/dvd_reader.h: No such file or directory
../libk9copy/k9common.h:30:30: error: dvdread/ifo_read.h: No such file or directory
../libk9copy/k9common.h:31:31: error: dvdread/ifo_print.h: No such file or directory
../libk9copy/k9common.h:32:30: error: dvdread/nav_read.h: No such file or directory
../libk9copy/k9dvdread.h:23: error: ISO C++ forbids declaration of 'dvd_file_t' with no type
../libk9copy/k9dvdread.h:23: error: expected ';' before '*' token
../libk9copy/k9dvdread.h:41: error: ISO C++ forbids declaration of 'dvd_reader_t' with no type
../libk9copy/k9dvdread.h:41: error: expected ';' before '*' token
../libk9copy/k9dvdread.h:53: error: ISO C++ forbids declaration of 'dvd_reader_t' with no type
../libk9copy/k9dvdread.h:53: error: expected ';' before '*' token
../libk9copy/k9dvdread.h:58: error: expected `;' before '}' token
../libk9copy/k9dvd.h:149: error: 'ifo_handle_t' has not been declared
../libk9copy/k9dvd.h:152: error: 'dvd_time_t' has not been declared
../libk9copy/k9dvd.h:158: error: 'ifo_handle_t' has not been declared
../libk9copy/k9ifo.h:38: error: ISO C++ forbids declaration of 'ifo_handle_t' with no type
../libk9copy/k9ifo.h:38: error: expected ';' before '*' token
../libk9copy/k9ifo.h:41: error: ISO C++ forbids declaration of 'ifo_handle_t' with no type
../libk9copy/k9ifo.h:41: error: expected ';' before '*' token
../libk9copy/k9ifo.h:42: error: 'pci_t' has not been declared
../libk9copy/k9ifo.h:47: error: ISO C++ forbids declaration of 'ifo_handle_t' with no type
../libk9copy/k9ifo.h:47: error: expected ';' before '*' token
../libk9copy/k9ifo.h:58: error: 'pgc_command_tbl_t' has not been declared
../libk9copy/k9ifo.h:59: error: 'pgc_program_map_t' has not been declared
../libk9copy/k9ifo.h:60: error: 'cell_playback_t' has not been declared
../libk9copy/k9ifo.h:61: error: 'cell_position_t' has not been declared
../libk9copy/k9ifo.h:62: error: 'pgc_t' has not been declared
../libk9copy/k9ifo.h:71: error: 'pgcit_t' has not been declared
../libk9copy/k9ifo.h:75: error: 'c_adt_t' has not been declared
../libk9copy/k9ifo.h:76: error: 'vobu_admap_t' has not been declared
../libk9copy/k9dvdbackup.h:58: error: 'cell_adr_t' was not declared in this scope
../libk9copy/k9dvdbackup.h:58: error: template argument 1 is invalid
../libk9copy/k9dvdbackup.h:110: error: 'ifo_handle_t' has not been declared
../libk9copy/k9dvdbackup.h:111: error: 'ifo_handle_t' has not been declared
k9vamps.cpp: In member function 'virtual void k9vamps::run()':
k9vamps.cpp:195: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'int k9vamps::lock(int)':
k9vamps.cpp:254: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::copy(int)':
k9vamps.cpp:269: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::check_pack(uchar*)':
k9vamps.cpp:328: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:331: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:339: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'int k9vamps::check_video_packet(uchar*)':
k9vamps.cpp:355: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:362: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:367: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:397: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:407: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'int k9vamps::new_private_1_type(uchar*)':
k9vamps.cpp:503: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::vap_leader()':
k9vamps.cpp:623: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:629: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::vap_trailer(int)':
k9vamps.cpp:666: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'int k9vamps::vap_phase1()':
k9vamps.cpp:727: warning: comparison between signed and unsigned integer expressions
k9vamps.cpp:737: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:785: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:791: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::vap_phase2(int)':
k9vamps.cpp:921: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:927: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::fatal(char*, ...)':
k9vamps.cpp:1049: warning: function might be possible candidate for 'printf' format attribute
make[2]: *** [k9vamps.lo] Error 1
make[2]: Leaving directory `/home/someguyouknow/Progrums/k9copy-1.0.4-2/k9copy-1.0.4-2/k9vamps'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/someguyouknow/Progrums/k9copy-1.0.4-2/k9copy-1.0.4-2'
make: *** [all] Error 2

```

and this is what i get when i do make install.....
```
Making install in k9vamps
make[1]: Entering directory `/home/someguyouknow/Progrums/k9copy-1.0.4-2/k9copy-1.0.4-2/k9vamps'
source='k9vamps.cpp' object='k9vamps.lo' libtool=yes \
        depfile='.deps/k9vamps.Plo' tmpdepfile='.deps/k9vamps.TPlo' \
        depmode=gcc3 /bin/sh ../admin/depcomp \
        /bin/sh ../libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../libk9copy -I. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -c -o k9vamps.lo `test -f 'k9vamps.cpp' || echo './'`k9vamps.cpp
In file included from k9vamps.h:15,
                 from k9vamps.cpp:13:
../libk9copy/k9common.h:28:31: error: dvdread/ifo_types.h: No such file or directory
../libk9copy/k9common.h:29:32: error: dvdread/dvd_reader.h: No such file or directory
../libk9copy/k9common.h:30:30: error: dvdread/ifo_read.h: No such file or directory
../libk9copy/k9common.h:31:31: error: dvdread/ifo_print.h: No such file or directory
../libk9copy/k9common.h:32:30: error: dvdread/nav_read.h: No such file or directory
../libk9copy/k9dvdread.h:23: error: ISO C++ forbids declaration of 'dvd_file_t' with no type
../libk9copy/k9dvdread.h:23: error: expected ';' before '*' token
../libk9copy/k9dvdread.h:41: error: ISO C++ forbids declaration of 'dvd_reader_t' with no type
../libk9copy/k9dvdread.h:41: error: expected ';' before '*' token
../libk9copy/k9dvdread.h:53: error: ISO C++ forbids declaration of 'dvd_reader_t' with no type
../libk9copy/k9dvdread.h:53: error: expected ';' before '*' token
../libk9copy/k9dvdread.h:58: error: expected `;' before '}' token
../libk9copy/k9dvd.h:149: error: 'ifo_handle_t' has not been declared
../libk9copy/k9dvd.h:152: error: 'dvd_time_t' has not been declared
../libk9copy/k9dvd.h:158: error: 'ifo_handle_t' has not been declared
../libk9copy/k9ifo.h:38: error: ISO C++ forbids declaration of 'ifo_handle_t' with no type
../libk9copy/k9ifo.h:38: error: expected ';' before '*' token
../libk9copy/k9ifo.h:41: error: ISO C++ forbids declaration of 'ifo_handle_t' with no type
../libk9copy/k9ifo.h:41: error: expected ';' before '*' token
../libk9copy/k9ifo.h:42: error: 'pci_t' has not been declared
../libk9copy/k9ifo.h:47: error: ISO C++ forbids declaration of 'ifo_handle_t' with no type
../libk9copy/k9ifo.h:47: error: expected ';' before '*' token
../libk9copy/k9ifo.h:58: error: 'pgc_command_tbl_t' has not been declared
../libk9copy/k9ifo.h:59: error: 'pgc_program_map_t' has not been declared
../libk9copy/k9ifo.h:60: error: 'cell_playback_t' has not been declared
../libk9copy/k9ifo.h:61: error: 'cell_position_t' has not been declared
../libk9copy/k9ifo.h:62: error: 'pgc_t' has not been declared
../libk9copy/k9ifo.h:71: error: 'pgcit_t' has not been declared
../libk9copy/k9ifo.h:75: error: 'c_adt_t' has not been declared
../libk9copy/k9ifo.h:76: error: 'vobu_admap_t' has not been declared
../libk9copy/k9dvdbackup.h:58: error: 'cell_adr_t' was not declared in this scope
../libk9copy/k9dvdbackup.h:58: error: template argument 1 is invalid
../libk9copy/k9dvdbackup.h:110: error: 'ifo_handle_t' has not been declared
../libk9copy/k9dvdbackup.h:111: error: 'ifo_handle_t' has not been declared
k9vamps.cpp: In member function 'virtual void k9vamps::run()':
k9vamps.cpp:195: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'int k9vamps::lock(int)':
k9vamps.cpp:254: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::copy(int)':
k9vamps.cpp:269: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::check_pack(uchar*)':
k9vamps.cpp:328: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:331: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:339: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'int k9vamps::check_video_packet(uchar*)':
k9vamps.cpp:355: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:362: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:367: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:397: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:407: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'int k9vamps::new_private_1_type(uchar*)':
k9vamps.cpp:503: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::vap_leader()':
k9vamps.cpp:623: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:629: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::vap_trailer(int)':
k9vamps.cpp:666: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'int k9vamps::vap_phase1()':
k9vamps.cpp:727: warning: comparison between signed and unsigned integer expressions
k9vamps.cpp:737: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:785: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:791: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::vap_phase2(int)':
k9vamps.cpp:921: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:927: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::fatal(char*, ...)':
k9vamps.cpp:1049: warning: function might be possible candidate for 'printf' format attribute
make[1]: *** [k9vamps.lo] Error 1
make[1]: Leaving directory `/home/someguyouknow/Progrums/k9copy-1.0.4-2/k9copy-1.0.4-2/k9vamps'
make: *** [install-recursive] Error 1

```

---

### Post by someguyouknow on 2006-08-10
nothing?.....

---

### Post by enjoyin on 2006-08-10
The way I installed k9copy was:
1. I loaded the Ubuntu Dapper wiki from [http://easylinux.info](http://easylinux.info) 
2. Then I followed the notes for HOW TO ADD EXTRA REPOSITORIES.
3. Opened a terminal and sudo apt-get update
4. Again in a terminal sudo apt-get install k9copy and presto you can find it in Applications -> Sound & Video.

Hope this helps and enjoy.

---

### Post by Ramses de Norre on 2006-08-10
And for the compiling: did you run ./configure??

---

### Post by someguyouknow on 2006-08-10
thanks guys.....
i have it now.....
i found the repository i was looking for....

thanks for you help though!!!

---

### Post by Cubby on 2008-01-17
[I]Hi,

You leave me hanging.:confused:  What repository?  Thanks for your time to anyone to help me install k9copy version 1.0.4-2.  I have the default repositories, plus the one from automatix2.

I seem to be getting similar results as this is what terminal states:[/I]

```
me@me-desktop:~$ cd Desktop k9copy-1.0.4-2
me@me-desktop:~/Desktop$ cd k9copy-1.0.4-2
me@me $ sh ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets ${MAKE}... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wnon-virtual-dtor... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -O0... yes
checking whether g++ supports -Wl,--no-undefined... yes
checking whether g++ supports -Wl,--allow-shlib-undefined... yes
not using lib directory suffix
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
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
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking if C++ programs can be compiled... yes
checking for strlcat... no
checking if strlcat needs custom prototype... yes - in libkdefakes
checking for strlcpy... no
checking if strlcpy needs custom prototype... yes - in libkdefakes
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... socklen_t
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking for poll in -lpoll... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking if res_init is available... yes
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for short... yes
checking size of short... 2
checking for long... yes
checking size of long... 4
checking for char *... yes
checking size of char *... 4
checking for dlopen in -ldl... (cached) yes
checking for shl_unload in -ldld... no
checking for size_t... yes
checking size of size_t... 4
checking for unsigned long... yes
checking size of unsigned long... 4
checking sizeof size_t == sizeof unsigned long... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... libraries /usr/lib, headers .
checking for IceConnectionNumber in -lICE... yes
checking for libXext... yes
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for perl... /usr/bin/perl
checking for Qt... libraries /usr/share/qt3/lib, headers /usr/share/qt3/include using -mt
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... libraries /usr/lib, headers /usr/include/kde
checking if UIC has KDE plugins available... yes
checking for KDE paths... defaults
checking for dcopidl... /usr/bin/dcopidl
checking for dcopidl2cpp... /usr/bin/dcopidl2cpp
checking for mcopidl... /usr/bin/mcopidl
checking for artsc-config... /usr/bin/artsc-config
checking for kde-config... /usr/bin/kde-config
checking for meinproc... /usr/bin/meinproc
checking for xmllint... /usr/bin/xmllint
checking whether byte ordering is bigendian... no
checking for MAXPATHLEN... 4096
checking for X86 architecture... yes
checking for 386 architecture... yes
checking for X86_64 architecture... no
checking if doc should be compiled... yes
checking if k9decmpeg should be compiled... yes
checking if k9vamps should be compiled... yes
checking if libk3bdevice should be compiled... yes
checking if libk9copy should be compiled... yes
checking if po should be compiled... yes
checking if src should be compiled... yes
configure: creating ./config.status
fast creating Makefile
fast creating doc/Makefile
fast creating k9decmpeg/Makefile
fast creating k9vamps/Makefile
fast creating libk3bdevice/Makefile
fast creating libk9copy/Makefile
fast creating po/Makefile
fast creating src/Makefile
config.pl: fast created 8 file(s).
config.status: creating config.h
config.status: executing depfiles commands

Good - your configure finished. Start make now

me#desktop software name$ make
cd . &&bin bash admin missing--run autoheader
autoheader: `config.h.in' is unchanged
touch ./config.h.in
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-recursive
make[1]: Entering directory `/home/me/Desktop/k9copy-1.0.4-2'
Making all in k9vamps
make[2]: Entering directory `/home/me/Desktop/k9copy-1.0.4-2/k9vamps'
source='k9vamps.cpp' object='k9vamps.lo' libtool=yes \
        depfile='.deps/k9vamps.Plo' tmpdepfile='.deps/k9vamps.TPlo' \
        depmode=gcc3 /bin/bash ../admin/depcomp \
        /bin/bash ../libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../libk9copy -I. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -c -o k9vamps.lo `test -f 'k9vamps.cpp' || echo './'`k9vamps.cpp
In file included from k9vamps.h:15,
                 from k9vamps.cpp:13:
../libk9copy/k9common.h:28:31: error: dvdread/ifo_types.h: No such file or directory
../libk9copy/k9common.h:29:32: error: dvdread/dvd_reader.h: No such file or directory
../libk9copy/k9common.h:30:30: error: dvdread/ifo_read.h: No such file or directory
../libk9copy/k9common.h:31:31: error: dvdread/ifo_print.h: No such file or directory
../libk9copy/k9common.h:32:30: error: dvdread/nav_read.h: No such file or directory
../libk9copy/k9dvdread.h:23: error: ISO C++ forbids declaration of 'dvd_file_t' with no type
../libk9copy/k9dvdread.h:23: error: expected ';' before '*' token
../libk9copy/k9dvdread.h:41: error: ISO C++ forbids declaration of 'dvd_reader_t' with no type
../libk9copy/k9dvdread.h:41: error: expected ';' before '*' token
../libk9copy/k9dvdread.h:53: error: ISO C++ forbids declaration of 'dvd_reader_t' with no type
../libk9copy/k9dvdread.h:53: error: expected ';' before '*' token
../libk9copy/k9dvdread.h:58: error: expected `;' before '}' token
../libk9copy/k9dvd.h:149: error: 'ifo_handle_t' has not been declared
../libk9copy/k9dvd.h:152: error: 'dvd_time_t' has not been declared
../libk9copy/k9dvd.h:158: error: 'ifo_handle_t' has not been declared
../libk9copy/k9ifo.h:38: error: ISO C++ forbids declaration of 'ifo_handle_t' with no type
../libk9copy/k9ifo.h:38: error: expected ';' before '*' token
../libk9copy/k9ifo.h:41: error: ISO C++ forbids declaration of 'ifo_handle_t' with no type
../libk9copy/k9ifo.h:41: error: expected ';' before '*' token
../libk9copy/k9ifo.h:42: error: 'pci_t' has not been declared
../libk9copy/k9ifo.h:47: error: ISO C++ forbids declaration of 'ifo_handle_t' with no type
../libk9copy/k9ifo.h:47: error: expected ';' before '*' token
../libk9copy/k9ifo.h:58: error: 'pgc_command_tbl_t' has not been declared
../libk9copy/k9ifo.h:59: error: 'pgc_program_map_t' has not been declared
../libk9copy/k9ifo.h:60: error: 'cell_playback_t' has not been declared
../libk9copy/k9ifo.h:61: error: 'cell_position_t' has not been declared
../libk9copy/k9ifo.h:62: error: 'pgc_t' has not been declared
../libk9copy/k9ifo.h:71: error: 'pgcit_t' has not been declared
../libk9copy/k9ifo.h:75: error: 'c_adt_t' has not been declared
../libk9copy/k9ifo.h:76: error: 'vobu_admap_t' has not been declared
../libk9copy/k9dvdbackup.h:58: error: 'cell_adr_t' was not declared in this scope
../libk9copy/k9dvdbackup.h:58: error: template argument 1 is invalid
../libk9copy/k9dvdbackup.h:110: error: 'ifo_handle_t' has not been declared
../libk9copy/k9dvdbackup.h:111: error: 'ifo_handle_t' has not been declared
k9vamps.cpp: In member function 'virtual void k9vamps::run()':
k9vamps.cpp:195: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'int k9vamps::lock(int)':
k9vamps.cpp:254: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::copy(int)':
k9vamps.cpp:269: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::check_pack(uchar*)':
k9vamps.cpp:328: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:331: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:339: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'int k9vamps::check_video_packet(uchar*)':
k9vamps.cpp:355: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:362: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:367: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:397: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:407: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'int k9vamps::new_private_1_type(uchar*)':
k9vamps.cpp:503: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::vap_leader()':
k9vamps.cpp:623: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:629: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::vap_trailer(int)':
k9vamps.cpp:666: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'int k9vamps::vap_phase1()':
k9vamps.cpp:727: warning: comparison between signed and unsigned integer expressions
k9vamps.cpp:737: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:785: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:791: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::vap_phase2(int)':
k9vamps.cpp:921: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp:927: warning: deprecated conversion from string constant to 'char*''
k9vamps.cpp: In member function 'void k9vamps::fatal(char*, ...)':
k9vamps.cpp:1049: warning: function might be possible candidate for 'printf' format attribute
make[2]: *** [k9vamps.lo] Error 1
make[2]: Leaving directory `/home/me/Desktop/k9copy-1.0.4-2/k9vamps'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/me/Desktop/k9copy-1.0.4-2'
make: *** [all] Error 2
me@meDesktop software name
```

---

### Post by wjston on 2008-01-17
> **Cubby said:**
> [I]Hi,

You leave me hanging.:confused:  What repository?  Thanks for your time to anyone to help me install k9copy version 1.0.4-2. 

Why install 1.0.4-2? Follow post #27 here to install the latest version:
[http://ubuntuforums.org/showthread.php?t=607991&page=3&highlight=k9copy](http://ubuntuforums.org/showthread.php?t=607991&page=3&highlight=k9copy)

---

### Post by Cubby on 2008-01-17
Oh, thank you wjston!  I just popped in here to say that I did manage to install the k9copy-1.0.4-2.tar.gz version using the below link information after installing with my dial-up connection on, though I don't know if I needed internet access while installing it.  Can you tell I'm a greenhorn?  Anyway, I un-commented two http repositories in my sources list.  I also had to install several packages as I got stuck and had to change a file permission to read and write for /usr/local as well as /usr to install some files, such as KDE.  This is what I followed:
[https://help.ubuntu.com/community/K9Copy?highlight=%28%28BuildingK9CopyfromSource%29%29](https://help.ubuntu.com/community/K9Copy?highlight=%28%28BuildingK9CopyfromSource%29%29)
and went to the link there Building K9Copy through Source

I was so excited, though I still need to probably do a bit of work before I try it out.  It's late, and I will do as you suggested tomorrow as I would like to get the latest version of this tool.  I thought that the said version I installed was the latest, though I know there is a new beta version.  

This all would probably have been a lot easier to do if I was running kubuntu, but anyway, I'm closer to my goal using Feisty Fawn Ubuntu.

I have dual boot with windows 2k, and the only reason I even open up that operating system is to use 3 wndws dvd editing/burning tools of rip it for me, shrink and nero.  That is why I'm trying to install the latest k9copy.  I am also trying out dvd::rip as well as xdvdshrink.  

I'm looking forward to trying out these software packages and seeing which one works best for me.

Thanks again! You are kind to write your suggestion.

Lisa Marie

---

