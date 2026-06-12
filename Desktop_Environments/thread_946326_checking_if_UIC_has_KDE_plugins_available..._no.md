---
title: "checking if UIC has KDE plugins available... no"
date: 2008-10-13
forum: Desktop Environments
---

### Post by abhayani on 2008-10-13
Hi Guys,

I am pretty new to Ubuntu and linux.

I am trying to install Twinkle SIP Phone on Ubuntu and I get below said error, but I have the kdelibs

[FONT="Courier New"][FONT="Courier New"]abhayani@abhayani-laptop:~/Downloads/twinkle/twinkle-1.3.2$ ./configure[/FONT]
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C preprocessor... gcc -E
checking how to run the C++ preprocessor... g++ -E
checking for ranlib... ranlib
checking for flex... no
checking for lex... no
checking for yywrap in -lfl... no
checking for yywrap in -ll... no
checking for bison... no
checking for byacc... no
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
checking whether strerror_r is declared... yes
checking for strerror_r... yes
checking whether strerror_r returns char *... yes
checking linux/types.h usability... yes
checking linux/types.h presence... yes
checking for linux/types.h... yes
checking for linux/errqueue.h... yes
checking for ccgnu2-config... /usr/local/bin/ccgnu2-config
checking for commoncpp2 version >= 1.6.0... yes
checking for pkg-config... /usr/bin/pkg-config
checking for libccrtp1 >= 1.6.0... yes
checking CCRTP_CFLAGS... -D_GNU_SOURCE -I/usr/local/include  
checking CCRTP_LIBS... -pthread -lccrtp1 -lccgnu2 -ldl -lrt  
checking for libxml-2.0... yes
checking XML2_CFLAGS... -I/usr/include/libxml2  
checking XML2_LIBS... -lxml2  
checking for qt-mt >= 3.3.0 qt-mt < 4.0... yes
checking QT_CFLAGS... -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_THREAD_SUPPORT -D_REENTRANT -I/usr/include/qt3  
checking QT_LIBS... -L/usr/X11R6/lib -lqt-mt -laudio -lXt -ljpeg -lpng -lz -lXi -lXrender -lXrandr -lXcursor -lXinerama -lXft -lfreetype -lfontconfig -lXext -lX11 -lm -lSM -lICE -ldl -lpthread  
checking value of $QTDIR... /home/abhayani/Downloads/qt-x11-free-3.3.8
checking for qmake... yes
checking for strlcat... no
checking if strlcat needs custom prototype... yes - in libkdefakes
checking for strlcpy... no
checking if strlcpy needs custom prototype... yes - in libkdefakes
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... yes
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking sys/bitypes.h usability... yes
checking sys/bitypes.h presence... yes
checking for sys/bitypes.h... yes
checking for poll in -lpoll... no
checking Carbon/Carbon.h usability... no
checking Carbon/Carbon.h presence... no
checking for Carbon/Carbon.h... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking for res_init... yes
checking if res_init needs custom prototype... no
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for short... yes
checking size of short... 2
checking for long... yes
checking size of long... 4
checking for char *... yes
checking size of char *... 4
checking for dlopen in -ldl... yes
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
not using lib directory suffix
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
checking for Qt... libraries /usr/share/qt3/lib, headers /home/abhayani/Downloads/qt-x11-free-3.3.8/include using -mt
checking for moc... /home/abhayani/Downloads/qt-x11-free-3.3.8/bin/moc
checking for uic... /home/abhayani/Downloads/qt-x11-free-3.3.8/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for lrelease... yes
configure: creating qtccxxincl.pro (include project file for Qt)
checking for kde-config... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking if C++ programs can be compiled... yes
checking for rpath... yes
checking for KDE... libraries /usr/lib, headers /usr/include/kde
checking if UIC has KDE plugins available... no
configure: error: you need to install kdelibs first.[/FONT]

---

