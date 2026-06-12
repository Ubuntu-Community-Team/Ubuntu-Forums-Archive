---
title: "make problem"
date: 2006-08-28
forum: Desktop Environments
---

### Post by mihalisla on 2006-08-28
Hello icannon make after ./configure in dapper 64 bit .I'm trying to install eagle-usb-2.3.2.tar.bz2.
here are the logs:
configure:
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes

checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for off_t... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for working volatile... yes
checking whether closedir returns void... no
checking whether gcc needs -traditional... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking for sys/socket.h... (cached) yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking return type of signal handlers... void
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for strftime... yes
checking for alarm... yes
checking for gettimeofday... yes
checking for memset... yes
checking for select... yes
checking for socket... yes
checking for strcspn... yes
checking for strdup... yes
checking for strerror... yes
checking for strncasecmp... yes
checking for strspn... yes
checking for strtol... yes
checking for ifconfig... yes
checking for route... yes
checking for pidof... yes
checking for dhclient... dhclient
checking for pppd... yes
checking for pppoe... no
checking for tclsh... yes
checking for wish... yes
checking for doc/man/eagleconfig.8... yes
checking for xsltproc... yes
   *** docbook stylesheets are missing, keeping prebuild version ***
checking for kernel version... 2.6.15-26-amd64-generic
checking for ifup... 1
checking for adictrl... no
checking for eaglectrl... no
checking for showstat... no
checking for eaglestat... no
checking for startadsl... no
checking for stopadsl... no
configure: creating ./config.status
config.status: creating Makefile.common

========================================================================
distribution detected				Debian

dhcp support					dhclient

pppd support					yes
  pppoa support					yes
  pppoe support					no  (runtime detection)

install eagleconnect (tcl/tk frontend)		yes

generate documentation				no
========================================================================

note: current gcc should be the same version as the one used to compile kernel.


make:
make -C driver && \
        make -C pppoa && \
        make -C utils/scripts && \
        make -C utils/eagleconnect && \
        make -C doc
make[1]: Entering directory `/opt/eagle-usb-2.0.0/driver'
USE_CMVS=0 make  -C /lib/modules/2.6.15-26-amd64-generic/build SUBDIRS=/opt/eagle-usb-2.0.0/driver modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-26-amd64-generic'
  CC [M]  /opt/eagle-usb-2.0.0/driver/eu_main.o
In file included from /opt/eagle-usb-2.0.0/driver/eagle-usb.h:30,
                 from /opt/eagle-usb-2.0.0/driver/eu_main.c:41:
/opt/eagle-usb-2.0.0/driver/eu_types.h:54:5: warning: "USE_CMVS" is not defined
/opt/eagle-usb-2.0.0/driver/eu_main.c: In function ‘eu_disconnect_postfirm’:
/opt/eagle-usb-2.0.0/driver/eu_main.c:955: error: ‘URB_ASYNC_UNLINK’ undeclared (first use in this function)
/opt/eagle-usb-2.0.0/driver/eu_main.c:955: error: (Each undeclared identifier is reported only once
/opt/eagle-usb-2.0.0/driver/eu_main.c:955: error: for each function it appears in.)
/opt/eagle-usb-2.0.0/driver/eu_main.c:1105:5: warning: "USE_CMVS" is not defined/opt/eagle-usb-2.0.0/driver/eu_main.c:1340:5: warning: "USE_CMVS" is not defined/opt/eagle-usb-2.0.0/driver/eu_main.c:1408:5: warning: "USE_CMVS" is not definedmake[3]: *** [/opt/eagle-usb-2.0.0/driver/eu_main.o] Error 1
make[2]: *** [_module_/opt/eagle-usb-2.0.0/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-26-amd64-generic'
make[1]: *** [eagle-usb.ko] Error 2
make[1]: Leaving directory `/opt/eagle-usb-2.0.0/driver'
make: *** [build] Error 2


I think that the kernel needs recompilation with current gcc4.0

1.how i recompile kernel with current installed gcc?
2.is there a guide cause i'm complete NEWBIE?
3.Is the procedure installing .bz2 , .gz files the same as ./configure, make, make install in ubuntu?

Thank you in advance for helping me uot:(

---

