---
title: "Installing tar- &quot;make&quot; is failing"
date: 2008-01-16
forum: Desktop Environments
---

### Post by osonegro on 2008-01-16
I am trying to install a program that came as a tar file.  I got it to configure but when I run "make" I get the following error messages:

-------------------------------------------------------------------------------------
make  all-recursive
make[1]: Entering directory `/usr/local/src/airsnort-0.2.7e'
Making all in src
make[2]: Entering directory `/usr/local/src/airsnort-0.2.7e/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -O2 -MT callbacks.o -MD -MP -MF ".deps/callbacks.Tpo" -c -o callbacks.o callbacks.c; \
        then mv -f ".deps/callbacks.Tpo" ".deps/callbacks.Po"; else rm -f ".deps/callbacks.Tpo"; exit 1; fi
callbacks.c:9:18: error: pcap.h: No such file or directory
In file included from PacketSource.h:31,
                 from callbacks.c:24:
/usr/include/linux/wireless.h:650: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:663: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:677: error: expected specifier-qualifier-list before ‘__s32’
/usr/include/linux/wireless.h:688: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:704: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:717: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:744: error: expected specifier-qualifier-list before ‘__u8’
/usr/include/linux/wireless.h:806: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:820: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:834: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:842: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:851: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:863: error: expected specifier-qualifier-list before ‘__u16’
/usr/include/linux/wireless.h:886: error: ‘IFNAMSIZ’ undeclared here (not in a function)
/usr/include/linux/wireless.h:901: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:945: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1046: error: expected specifier-qualifier-list before ‘__u32’
/usr/include/linux/wireless.h:1064: error: expected specifier-qualifier-list before ‘__u16’
In file included from callbacks.c:24:
PacketSource.h:153: error: expected specifier-qualifier-list before ‘pcap_t’
PacketSource.h:178: warning: ‘struct pcap_pkthdr’ declared inside parameter list
PacketSource.h:178: warning: its scope is only this definition or declaration, which is probably not what you want
PacketSource.h:179: warning: ‘struct pcap_pkthdr’ declared inside parameter list
callbacks.c:79: error: ‘PCAP_ERRBUF_SIZE’ undeclared here (not in a function)
callbacks.c: In function ‘fillDeviceList’:
callbacks.c:121: error: storage size of ‘ir’ isn’t known
callbacks.c:129: error: ‘IFF_LOOPBACK’ undeclared (first use in this function)
callbacks.c:129: error: (Each undeclared identifier is reported only once
callbacks.c:129: error: for each function it appears in.)
make[2]: *** [callbacks.o] Error 1
make[2]: Leaving directory `/usr/local/src/airsnort-0.2.7e/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/airsnort-0.2.7e'
make: *** [all] Error 2
--------------------------------------------------------------------------------
Lots of errors but I don't know where to go from here...  HELP!
r

---

### Post by AndyCooll on 2008-01-16
Have you installed build-essential?

:cool:

---

### Post by osonegro on 2008-01-18
According to Snaptic package manager "build-essential" is already installed.

For this particular program I found a "deb" for it but I'd still like to continue this thread so that in the future I know what to do.

---

### Post by rattking on 2008-01-18
Hi
you can see the errors start here

callbacks.c:9:18: error: pcap.h: No such file or directory

apt-file is useful for finding what package contains that file
apt-file search pcap.h
finds a few packages but i bet libpcap0.8-dev is the one your in need of
-dev packages are required when compiling from source

ps if the package you want to compile is already in the repo you can cheat and install all dependencies with the command
apt-get build-dep airsnort
hope that helps!

---

