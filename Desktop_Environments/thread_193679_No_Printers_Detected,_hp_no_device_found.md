---
title: "No Printers Detected, hp no_device_found"
date: 2006-06-10
forum: Desktop Environments
---

### Post by fonsv on 2006-06-10
Hello, 

After upgrading to Dapper my printer (HP 3816, usb) does not work anymore. Trying to reinstall does not work. System->Administration->Printing->add new printer results only in No Printers Detected and for the port hp no_device_found.

I tried reinstalling the whole lot of printing drivers, cups etc.
No results...
I also tried to recompile hlip but that would not work due to a missing cups-devel package which I could not find.

Any ideas on how to get my printer working again?

Thanks alot,

Fons

---

### Post by yager on 2006-06-10
[QUOTE=fonsv]
I also tried to recompile hlip but that would not work due to a missing cups-devel package which I could not find.[/QUOTE]

I had a similar issue and sorted out which packages were missing.  Check this thread where I documented the change to the HPLIP instructions that were required to compile HPLIP.

[http://www.ubuntuforums.org/showthread.php?t=169629](http://www.ubuntuforums.org/showthread.php?t=169629)

I hope this helps.  I too lost my printer going to Dapper, but now I found it.

---

### Post by fonsv on 2006-06-10
I tried to do this on my system as well.  ./configure --prefix=/usr works just fine, but sudo make returns an error at the end:
hpiod.o:1: error: Cannot open input file

The complete output was: 

Making all in .
make[1]: Entering directory `/home/fons/hplip-0.9.10'
source='io/hpiod/hpiod.cpp' object='hpiod.o' libtool=no \
        DEPDIR=.deps depmode=none /bin/sh ./depcomp \
        gpp -DPACKAGE_NAME=\"HP\ Linux\ Imaging\ and\ Printing\" -DPACKAGE_TARNAME=\"hplip\" -DPACKAGE_VERSION=\"0.9.10\" -DPACKAGE_STRING=\"HP\ Linux\ Imaging\ and\ Printing\ 0.9.10\" -DPACKAGE_BUGREPORT=\"0.9.10.4\" -DPACKAGE=\"hplip\" -DVERSION=\"0.9.10\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_LIBPTHREAD=1 -DHAVE_LIBCRYPTO=1 -DHAVE_LIBUSB=1 -DSTDC_HEADERS=1 -DHAVE_CUPS_CUPS_H=1 -DHAVE_NET_SNMP_NET_SNMP_CONFIG_H=1 -DHAVE_PPORT=1 -DHAVE_LIBSNMP=1  -I. -I. -Iprnt/hpijs -Iip     -c -o hpiod.o `test -f 'io/hpiod/hpiod.cpp' || echo './'`io/hpiod/hpiod.cpp
hpiod.o:1: error: Cannot open input file
make[1]: *** [hpiod.o] Error 1
make[1]: Leaving directory `/home/fons/hplip-0.9.10'
make: *** [all-recursive] Error 1

---

