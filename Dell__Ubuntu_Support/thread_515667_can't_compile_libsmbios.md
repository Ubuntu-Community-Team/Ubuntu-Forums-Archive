---
title: "can't compile libsmbios"
date: 2007-08-02
forum: Dell  Ubuntu Support
---

### Post by Nunslaughter on 2007-08-02
i tried to compile libsmbios 0.13.8 because you can change the dell xps m1710 leds with it, but i have some problems...here the outputs:

```
timo@timo-laptop:~/libsmbios-0.13.8$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for cppunit-config... no
checking for Cppunit - version >= 1.9.6... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C preprocessor... gcc -E
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
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
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for a BSD-compatible install... /usr/bin/install -c
checking for ANSI C header files... (cached) yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/file.h usability... yes
checking sys/file.h presence... yes
checking for sys/file.h... yes
checking for unistd.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for off_t... yes
checking for size_t... yes
checking for ptrdiff_t... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for getpagesize... (cached) yes
checking for memmove... yes
checking for memset... yes
checking for munmap... yes
checking for strerror... yes
checking for strndup... yes
checking for strtol... yes
checking for strtoul... yes
checking for doxygen... no
checking for dot... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating include/smbios/version.h
config.status: creating doc/full-documentation.dox
config.status: creating doc/interface-only.dox
config.status: creating libsmbios.spec
config.status: executing depfiles commands
 
```

```
timo@timo-laptop:~/libsmbios-0.13.8$ make
make[1]: Map '/home/timo/libsmbios-0.13.8' wordt binnengegaan
if /bin/bash ./libtool --tag=CXX --mode=compile g++ -DPACKAGE_NAME=\"libsmbios\" -DPACKAGE_TARNAME=\"libsmbios\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libsmbios\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1 -DHAVE_LIBINTL_H=1 -DHAVE_LIMITS_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_SYS_FILE_H=1 -DHAVE_UNISTD_H=1 -DHAVE__BOOL=1 -DHAVE_STDBOOL_H=1 -DHAVE_PTRDIFF_T=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_STDLIB_H=1 -DHAVE_UNISTD_H=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MMAP=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MEMMOVE=1 -DHAVE_MEMSET=1 -DHAVE_MUNMAP=1 -DHAVE_STRERROR=1 -DHAVE_STRNDUP=1 -DHAVE_STRTOL=1 -DHAVE_STRTOUL=1 -DVERSION=\"0.13.8\" -DPACKAGE_VERSION=\"0.13.8\" -DPACKAGE_STRING=\"libsmbios\ 0.13.8\"  -I. -I. -I./include -I./include   -I./libraries/common -I./libraries/common  -g -O2 -MT libraries/systeminfo/libraries_libsmbios_la-System.lo -MD -MP -MF "libraries/systeminfo/.deps/libraries_libsmbios_la-System.Tpo" -c -o libraries/systeminfo/libraries_libsmbios_la-System.lo `test -f 'libraries/systeminfo/System.cpp' || echo './'`libraries/systeminfo/System.cpp; \
        then mv -f "libraries/systeminfo/.deps/libraries_libsmbios_la-System.Tpo" "libraries/systeminfo/.deps/libraries_libsmbios_la-System.Plo"; else rm -f "libraries/systeminfo/.deps/libraries_libsmbios_la-System.Tpo"; exit 1; fi
 g++ -DPACKAGE_NAME=\"libsmbios\" -DPACKAGE_TARNAME=\"libsmbios\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libsmbios\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1 -DHAVE_LIBINTL_H=1 -DHAVE_LIMITS_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_SYS_FILE_H=1 -DHAVE_UNISTD_H=1 -DHAVE__BOOL=1 -DHAVE_STDBOOL_H=1 -DHAVE_PTRDIFF_T=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_STDLIB_H=1 -DHAVE_UNISTD_H=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MMAP=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MEMMOVE=1 -DHAVE_MEMSET=1 -DHAVE_MUNMAP=1 -DHAVE_STRERROR=1 -DHAVE_STRNDUP=1 -DHAVE_STRTOL=1 -DHAVE_STRTOUL=1 -DVERSION=\"0.13.8\" -DPACKAGE_VERSION=\"0.13.8\" "-DPACKAGE_STRING=\"libsmbios 0.13.8\"" -I. -I. -I./include -I./include -I./libraries/common -I./libraries/common -g -O2 -MT libraries/systeminfo/libraries_libsmbios_la-System.lo -MD -MP -MF libraries/systeminfo/.deps/libraries_libsmbios_la-System.Tpo -c libraries/systeminfo/System.cpp  -fPIC -DPIC -o libraries/systeminfo/.libs/libraries_libsmbios_la-System.o
 g++ -DPACKAGE_NAME=\"libsmbios\" -DPACKAGE_TARNAME=\"libsmbios\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libsmbios\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1 -DHAVE_LIBINTL_H=1 -DHAVE_LIMITS_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_SYS_FILE_H=1 -DHAVE_UNISTD_H=1 -DHAVE__BOOL=1 -DHAVE_STDBOOL_H=1 -DHAVE_PTRDIFF_T=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_STDLIB_H=1 -DHAVE_UNISTD_H=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MMAP=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MEMMOVE=1 -DHAVE_MEMSET=1 -DHAVE_MUNMAP=1 -DHAVE_STRERROR=1 -DHAVE_STRNDUP=1 -DHAVE_STRTOL=1 -DHAVE_STRTOUL=1 -DVERSION=\"0.13.8\" -DPACKAGE_VERSION=\"0.13.8\" "-DPACKAGE_STRING=\"libsmbios 0.13.8\"" -I. -I. -I./include -I./include -I./libraries/common -I./libraries/common -g -O2 -MT libraries/systeminfo/libraries_libsmbios_la-System.lo -MD -MP -MF libraries/systeminfo/.deps/libraries_libsmbios_la-System.Tpo -c libraries/systeminfo/System.cpp -o libraries/systeminfo/libraries_libsmbios_la-System.o >/dev/null 2>&1
/bin/bash ./libtool --tag=CXX --mode=link g++  -g -O2   -o libraries/libsmbios.la -rpath /usr/local/lib -version-info 1:13:0 libraries/cmos/libraries_libsmbios_la-CmosRW.lo libraries/cmos/libraries_libsmbios_la-CmosRWFactory.lo libraries/cmos/libraries_libsmbios_la-CmosRW_LinuxIO.lo libraries/common/libraries_libsmbios_la-ascii2enUS_scancode.lo libraries/common/libraries_libsmbios_la-Observer.lo libraries/memory/libraries_libsmbios_la-Memory.lo libraries/memory/libraries_libsmbios_la-Memory_Linux.lo libraries/rbu/libraries_libsmbios_la-RbuHdr.lo libraries/rbu/libraries_libsmbios_la-Rbu_Linux.lo libraries/smbios/libraries_libsmbios_la-SmbiosFactory.lo libraries/smbios/libraries_libsmbios_la-SmbiosItem.lo libraries/smbios/libraries_libsmbios_la-SmbiosStrategy.lo libraries/smbios/libraries_libsmbios_la-SmbiosStrategy_Linux.lo libraries/smbios/libraries_libsmbios_la-SmbiosTable.lo libraries/smbios/libraries_libsmbios_la-SmbiosTableIterator.lo libraries/smbios/libraries_libsmbios_la-SmbiosWorkaround.lo libraries/smi/libraries_libsmbios_la-Smi.lo libraries/smi/libraries_libsmbios_la-SmiFactory.lo libraries/smi/libraries_libsmbios_la-Smi_Linux.lo libraries/systeminfo/libraries_libsmbios_la-IdByte.lo libraries/systeminfo/libraries_libsmbios_la-SysInfoError.lo libraries/systeminfo/libraries_libsmbios_la-System.lo libraries/systeminfo/libraries_libsmbios_la-SystemDetect.lo libraries/token/libraries_libsmbios_la-checksum.lo libraries/token/libraries_libsmbios_la-Token.lo libraries/token/libraries_libsmbios_la-TokenD4.lo libraries/token/libraries_libsmbios_la-TokenD5.lo libraries/token/libraries_libsmbios_la-TokenD6.lo libraries/token/libraries_libsmbios_la-TokenDA.lo libraries/token/libraries_libsmbios_la-TokenTable.lo libraries/token/libraries_libsmbios_la-TokenTableFactory.lo libraries/token/libraries_libsmbios_la-TokenTableIterator.lo  
rm -fr  libraries/.libs/libsmbios.a libraries/.libs/libsmbios.la libraries/.libs/libsmbios.lai libraries/.libs/libsmbios.so libraries/.libs/libsmbios.so.1 libraries/.libs/libsmbios.so.1.0.13
g++ -shared -nostdlib /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.1.2/crtbeginS.o  libraries/cmos/.libs/libraries_libsmbios_la-CmosRW.o libraries/cmos/.libs/libraries_libsmbios_la-CmosRWFactory.o libraries/cmos/.libs/libraries_libsmbios_la-CmosRW_LinuxIO.o libraries/common/.libs/libraries_libsmbios_la-ascii2enUS_scancode.o libraries/common/.libs/libraries_libsmbios_la-Observer.o libraries/memory/.libs/libraries_libsmbios_la-Memory.o libraries/memory/.libs/libraries_libsmbios_la-Memory_Linux.o libraries/rbu/.libs/libraries_libsmbios_la-RbuHdr.o libraries/rbu/.libs/libraries_libsmbios_la-Rbu_Linux.o libraries/smbios/.libs/libraries_libsmbios_la-SmbiosFactory.o libraries/smbios/.libs/libraries_libsmbios_la-SmbiosItem.o libraries/smbios/.libs/libraries_libsmbios_la-SmbiosStrategy.o libraries/smbios/.libs/libraries_libsmbios_la-SmbiosStrategy_Linux.o libraries/smbios/.libs/libraries_libsmbios_la-SmbiosTable.o libraries/smbios/.libs/libraries_libsmbios_la-SmbiosTableIterator.o libraries/smbios/.libs/libraries_libsmbios_la-SmbiosWorkaround.o libraries/smi/.libs/libraries_libsmbios_la-Smi.o libraries/smi/.libs/libraries_libsmbios_la-SmiFactory.o libraries/smi/.libs/libraries_libsmbios_la-Smi_Linux.o libraries/systeminfo/.libs/libraries_libsmbios_la-IdByte.o libraries/systeminfo/.libs/libraries_libsmbios_la-SysInfoError.o libraries/systeminfo/.libs/libraries_libsmbios_la-System.o libraries/systeminfo/.libs/libraries_libsmbios_la-SystemDetect.o libraries/token/.libs/libraries_libsmbios_la-checksum.o libraries/token/.libs/libraries_libsmbios_la-Token.o libraries/token/.libs/libraries_libsmbios_la-TokenD4.o libraries/token/.libs/libraries_libsmbios_la-TokenD5.o libraries/token/.libs/libraries_libsmbios_la-TokenD6.o libraries/token/.libs/libraries_libsmbios_la-TokenDA.o libraries/token/.libs/libraries_libsmbios_la-TokenTable.o libraries/token/.libs/libraries_libsmbios_la-TokenTableFactory.o libraries/token/.libs/libraries_libsmbios_la-TokenTableIterator.o  -L/usr/lib/gcc/i486-linux-gnu/4.1.2 -L/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib -L/lib/../lib -L/usr/lib/../lib -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/i486-linux-gnu/4.1.2/crtendS.o /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crtn.o  -Wl,-soname -Wl,libsmbios.so.1 -o libraries/.libs/libsmbios.so.1.0.13
(cd libraries/.libs && rm -f libsmbios.so.1 && ln -s libsmbios.so.1.0.13 libsmbios.so.1)
(cd libraries/.libs && rm -f libsmbios.so && ln -s libsmbios.so.1.0.13 libsmbios.so)
ar cru libraries/.libs/libsmbios.a  libraries/cmos/libraries_libsmbios_la-CmosRW.o libraries/cmos/libraries_libsmbios_la-CmosRWFactory.o libraries/cmos/libraries_libsmbios_la-CmosRW_LinuxIO.o libraries/common/libraries_libsmbios_la-ascii2enUS_scancode.o libraries/common/libraries_libsmbios_la-Observer.o libraries/memory/libraries_libsmbios_la-Memory.o libraries/memory/libraries_libsmbios_la-Memory_Linux.o libraries/rbu/libraries_libsmbios_la-RbuHdr.o libraries/rbu/libraries_libsmbios_la-Rbu_Linux.o libraries/smbios/libraries_libsmbios_la-SmbiosFactory.o libraries/smbios/libraries_libsmbios_la-SmbiosItem.o libraries/smbios/libraries_libsmbios_la-SmbiosStrategy.o libraries/smbios/libraries_libsmbios_la-SmbiosStrategy_Linux.o libraries/smbios/libraries_libsmbios_la-SmbiosTable.o libraries/smbios/libraries_libsmbios_la-SmbiosTableIterator.o libraries/smbios/libraries_libsmbios_la-SmbiosWorkaround.o libraries/smi/libraries_libsmbios_la-Smi.o libraries/smi/libraries_libsmbios_la-SmiFactory.o libraries/smi/libraries_libsmbios_la-Smi_Linux.o libraries/systeminfo/libraries_libsmbios_la-IdByte.o libraries/systeminfo/libraries_libsmbios_la-SysInfoError.o libraries/systeminfo/libraries_libsmbios_la-System.o libraries/systeminfo/libraries_libsmbios_la-SystemDetect.o libraries/token/libraries_libsmbios_la-checksum.o libraries/token/libraries_libsmbios_la-Token.o libraries/token/libraries_libsmbios_la-TokenD4.o libraries/token/libraries_libsmbios_la-TokenD5.o libraries/token/libraries_libsmbios_la-TokenD6.o libraries/token/libraries_libsmbios_la-TokenDA.o libraries/token/libraries_libsmbios_la-TokenTable.o libraries/token/libraries_libsmbios_la-TokenTableFactory.o libraries/token/libraries_libsmbios_la-TokenTableIterator.o
ranlib libraries/.libs/libsmbios.a
creating libraries/libsmbios.la
(cd libraries/.libs && rm -f libsmbios.la && ln -s ../libsmbios.la libsmbios.la)
/bin/bash: xml2-config: opdracht niet gevonden
if /bin/bash ./libtool --tag=CXX --mode=compile g++ -DPACKAGE_NAME=\"libsmbios\" -DPACKAGE_TARNAME=\"libsmbios\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libsmbios\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1 -DHAVE_LIBINTL_H=1 -DHAVE_LIMITS_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_SYS_FILE_H=1 -DHAVE_UNISTD_H=1 -DHAVE__BOOL=1 -DHAVE_STDBOOL_H=1 -DHAVE_PTRDIFF_T=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_STDLIB_H=1 -DHAVE_UNISTD_H=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MMAP=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MEMMOVE=1 -DHAVE_MEMSET=1 -DHAVE_MUNMAP=1 -DHAVE_STRERROR=1 -DHAVE_STRNDUP=1 -DHAVE_STRTOL=1 -DHAVE_STRTOUL=1 -DVERSION=\"0.13.8\" -DPACKAGE_VERSION=\"0.13.8\" -DPACKAGE_STRING=\"libsmbios\ 0.13.8\"  -I. -I. -I./include -I./include    -DLIBXML2=1 -DLIBXERCES=2 -DXMLUTILS=1 -I./libraries/common -I./libraries/common  -g -O2 -MT libraries/xml_libxml2/libraries_libsmbiosxml_la-SmbiosXml.lo -MD -MP -MF "libraries/xml_libxml2/.deps/libraries_libsmbiosxml_la-SmbiosXml.Tpo" -c -o libraries/xml_libxml2/libraries_libsmbiosxml_la-SmbiosXml.lo `test -f 'libraries/xml_libxml2/SmbiosXml.cpp' || echo './'`libraries/xml_libxml2/SmbiosXml.cpp; \
        then mv -f "libraries/xml_libxml2/.deps/libraries_libsmbiosxml_la-SmbiosXml.Tpo" "libraries/xml_libxml2/.deps/libraries_libsmbiosxml_la-SmbiosXml.Plo"; else rm -f "libraries/xml_libxml2/.deps/libraries_libsmbiosxml_la-SmbiosXml.Tpo"; exit 1; fi
 g++ -DPACKAGE_NAME=\"libsmbios\" -DPACKAGE_TARNAME=\"libsmbios\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libsmbios\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1 -DHAVE_LIBINTL_H=1 -DHAVE_LIMITS_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_SYS_FILE_H=1 -DHAVE_UNISTD_H=1 -DHAVE__BOOL=1 -DHAVE_STDBOOL_H=1 -DHAVE_PTRDIFF_T=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_STDLIB_H=1 -DHAVE_UNISTD_H=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MMAP=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MEMMOVE=1 -DHAVE_MEMSET=1 -DHAVE_MUNMAP=1 -DHAVE_STRERROR=1 -DHAVE_STRNDUP=1 -DHAVE_STRTOL=1 -DHAVE_STRTOUL=1 -DVERSION=\"0.13.8\" -DPACKAGE_VERSION=\"0.13.8\" "-DPACKAGE_STRING=\"libsmbios 0.13.8\"" -I. -I. -I./include -I./include -DLIBXML2=1 -DLIBXERCES=2 -DXMLUTILS=1 -I./libraries/common -I./libraries/common -g -O2 -MT libraries/xml_libxml2/libraries_libsmbiosxml_la-SmbiosXml.lo -MD -MP -MF libraries/xml_libxml2/.deps/libraries_libsmbiosxml_la-SmbiosXml.Tpo -c libraries/xml_libxml2/SmbiosXml.cpp  -fPIC -DPIC -o libraries/xml_libxml2/.libs/libraries_libsmbiosxml_la-SmbiosXml.o
In file included from libraries/xml_libxml2/SmbiosXmlImpl.h:25,
                 from libraries/xml_libxml2/SmbiosXml.cpp:26:
libraries/xml_libxml2/XmlUtils.h:24:30: error: libxml/xmlmemory.h: No such file or directory
libraries/xml_libxml2/XmlUtils.h:25:27: error: libxml/parser.h: No such file or directory
libraries/xml_libxml2/XmlUtils.h:114: error: expected ',' or '...' before '*' token
libraries/xml_libxml2/XmlUtils.h:114: error: ISO C++ forbids declaration of 'xmlNode' with no type
libraries/xml_libxml2/XmlUtils.h:117: error: 'xmlNodePtr' does not name a type
libraries/xml_libxml2/XmlUtils.h:118: error: 'xmlNodePtr' does not name a type
libraries/xml_libxml2/XmlUtils.h:120: error: 'xmlNodePtr' was not declared in this scope
libraries/xml_libxml2/XmlUtils.h:121: error: 'xmlNodePtr' was not declared in this scope
libraries/xml_libxml2/XmlUtils.h:121: error: expected primary-expression before 'const'
libraries/xml_libxml2/XmlUtils.h:121: error: expected primary-expression before 'int'
libraries/xml_libxml2/XmlUtils.h:121: error: initializer expression list treated as compound expression
libraries/xml_libxml2/SmbiosXmlImpl.h:49: error: ISO C++ forbids declaration of 'xmlDoc' with no type
libraries/xml_libxml2/SmbiosXmlImpl.h:49: error: expected ';' before '*' token
libraries/xml_libxml2/SmbiosXmlImpl.h:66: error: ISO C++ forbids declaration of 'xmlDoc' with no type
libraries/xml_libxml2/SmbiosXmlImpl.h:66: error: expected ';' before '*' token
libraries/xml_libxml2/SmbiosXml.cpp:113: error: expected constructor, destructor, or type conversion before '*' token
libraries/xml_libxml2/SmbiosXml.cpp:139: error: variable or field 'validateSmbiosXmlDoc' declared void
libraries/xml_libxml2/SmbiosXml.cpp:139: error: 'xmlDoc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:139: error: 'doc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:140: error: expected ',' or ';' before '{' token
libraries/xml_libxml2/SmbiosXml.cpp:174: error: expected ',' or '...' before '*' token
libraries/xml_libxml2/SmbiosXml.cpp:174: error: ISO C++ forbids declaration of 'xmlNode' with no type
libraries/xml_libxml2/SmbiosXml.cpp: In function 'void smbios::verifyElementAttr(int)':
libraries/xml_libxml2/SmbiosXml.cpp:176: error: 'element' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:176: error: 'elementName' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:177: error: 'value' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp: At global scope:
libraries/xml_libxml2/SmbiosXml.cpp:182: error: expected ',' or '...' before '*' token
libraries/xml_libxml2/SmbiosXml.cpp:182: error: ISO C++ forbids declaration of 'xmlNode' with no type
libraries/xml_libxml2/SmbiosXml.cpp: In function 'void smbios::verifyElementAttr(int)':
libraries/xml_libxml2/SmbiosXml.cpp:182: error: redefinition of 'void smbios::verifyElementAttr(int)'
libraries/xml_libxml2/SmbiosXml.cpp:174: error: 'void smbios::verifyElementAttr(int)' previously defined here
libraries/xml_libxml2/SmbiosXml.cpp:184: error: 'element' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:184: error: 'elementName' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:185: error: 'size' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp: At global scope:
libraries/xml_libxml2/SmbiosXml.cpp:189: error: 'xmlDoc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:189: error: 'doc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:189: error: expected primary-expression before 'const'
libraries/xml_libxml2/SmbiosXml.cpp:189: error: initializer expression list treated as compound expression
libraries/xml_libxml2/SmbiosXml.cpp:190: error: expected ',' or ';' before '{' token
libraries/xml_libxml2/SmbiosXml.cpp:198: error: expected ',' or '...' before '*' token
libraries/xml_libxml2/SmbiosXml.cpp:198: error: ISO C++ forbids declaration of 'xmlDoc' with no type
libraries/xml_libxml2/SmbiosXml.cpp: In function 'const std::string smbios::getStringForType(int)':
libraries/xml_libxml2/SmbiosXml.cpp:201: error: 'xmlNode' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:201: error: 'elem' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:204: error: expected type-specifier before 'xmlDocPtr'
libraries/xml_libxml2/SmbiosXml.cpp:204: error: expected `>' before 'xmlDocPtr'
libraries/xml_libxml2/SmbiosXml.cpp:204: error: expected `(' before 'xmlDocPtr'
libraries/xml_libxml2/SmbiosXml.cpp:204: error: 'xmlDocPtr' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:204: error: 'doc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:204: error: 'searchForType' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:204: error: 'xmlDocGetRootElement' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:208: error: expected type-specifier before 'xmlDocPtr'
libraries/xml_libxml2/SmbiosXml.cpp:208: error: expected `>' before 'xmlDocPtr'
libraries/xml_libxml2/SmbiosXml.cpp:208: error: expected `(' before 'xmlDocPtr'
libraries/xml_libxml2/SmbiosXml.cpp:208: error: 'xmlDocPtr' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:208: error: 'doc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:208: error: 'xmlDocGetRootElement' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp: In constructor 'smbios::SmbiosTableXml::SmbiosTableXml()':
libraries/xml_libxml2/SmbiosXml.cpp:223: error: class 'smbios::SmbiosTableXml' does not have any field named 'doc'
libraries/xml_libxml2/SmbiosXml.cpp:225: error: 'LIBXML_TEST_VERSION' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp: In constructor 'smbios::SmbiosTableXml::SmbiosTableXml(std::vector<smbios::SmbiosStrategy*, std::allocator<smbios::SmbiosStrategy*> >, bool)':
libraries/xml_libxml2/SmbiosXml.cpp:230: error: class 'smbios::SmbiosTableXml' does not have any field named 'doc'
libraries/xml_libxml2/SmbiosXml.cpp:232: error: 'LIBXML_TEST_VERSION' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp: In destructor 'virtual smbios::SmbiosTableXml::~SmbiosTableXml()':
libraries/xml_libxml2/SmbiosXml.cpp:242: error: 'doc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:243: error: 'xmlFreeDoc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp: In member function 'void smbios::SmbiosTableXml::setXmlFilePath(std::string)':
libraries/xml_libxml2/SmbiosXml.cpp:260: error: 'xmlSetGenericErrorFunc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:265: error: 'xmlDoc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:265: error: 'newdoc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:265: error: 'getSmbiosXmlDoc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:266: error: 'smbios::validateSmbiosXmlDoc' cannot be used as a function
libraries/xml_libxml2/SmbiosXml.cpp:273: error: 'doc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:274: error: 'xmlFreeDoc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:278: error: 'doc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp: At global scope:
libraries/xml_libxml2/SmbiosXml.cpp:289: error: expected initializer before '*' token
libraries/xml_libxml2/SmbiosXml.cpp: In member function 'int smbios::SmbiosTableXml::getTypeForString(std::string) const':
libraries/xml_libxml2/SmbiosXml.cpp:296: error: 'doc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:296: error: 'smbios::getTypeForString' cannot be used as a function
libraries/xml_libxml2/SmbiosXml.cpp: In member function 'const std::string smbios::SmbiosTableXml::getStringForType(int) const':
libraries/xml_libxml2/SmbiosXml.cpp:302: error: 'doc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp: In function 'void smbios::getData_UsingXml(const smbios::ISmbiosItem&, std::string, void*, size_t)':
libraries/xml_libxml2/SmbiosXml.cpp:327: error: 'xmlNode' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:327: error: 'element' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:336: error: expected initializer before '*' token
libraries/xml_libxml2/SmbiosXml.cpp:339: error: 'Structure' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:339: error: expected type-specifier before 'xmlDocPtr'
libraries/xml_libxml2/SmbiosXml.cpp:339: error: expected `>' before 'xmlDocPtr'
libraries/xml_libxml2/SmbiosXml.cpp:339: error: expected `(' before 'xmlDocPtr'
libraries/xml_libxml2/SmbiosXml.cpp:339: error: 'xmlDocPtr' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:339: error: 'doc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:339: error: 'xmlDocGetRootElement' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:340: error: 'findElement' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:346: error: 'xmlutils::getNumberFromXmlAttr' cannot be used as a function
libraries/xml_libxml2/SmbiosXml.cpp: In function 'const char* smbios::getString_FromItem(const smbios::ISmbiosItem&, std::string)':
libraries/xml_libxml2/SmbiosXml.cpp:379: error: 'xmlNode' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:379: error: 'element' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:388: error: expected initializer before '*' token
libraries/xml_libxml2/SmbiosXml.cpp:391: error: 'Structure' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:391: error: expected type-specifier before 'xmlDocPtr'
libraries/xml_libxml2/SmbiosXml.cpp:391: error: expected `>' before 'xmlDocPtr'
libraries/xml_libxml2/SmbiosXml.cpp:391: error: expected `(' before 'xmlDocPtr'
libraries/xml_libxml2/SmbiosXml.cpp:391: error: 'xmlDocPtr' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:391: error: 'doc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:391: error: 'xmlDocGetRootElement' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:392: error: 'findElement' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:401: error: 'xmlutils::getNumberFromXmlAttr' cannot be used as a function
libraries/xml_libxml2/SmbiosXml.cpp: In function 'void* smbios::getBits_FromItem(const smbios::ISmbiosItem&, std::string, std::string, void*)':
libraries/xml_libxml2/SmbiosXml.cpp:406: error: 'xmlNode' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:406: error: 'bitElement' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:407: error: 'fieldElement' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:416: error: expected initializer before '*' token
libraries/xml_libxml2/SmbiosXml.cpp:420: error: 'Structure' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:420: error: expected type-specifier before 'xmlDocPtr'
libraries/xml_libxml2/SmbiosXml.cpp:420: error: expected `>' before 'xmlDocPtr'
libraries/xml_libxml2/SmbiosXml.cpp:420: error: expected `(' before 'xmlDocPtr'
libraries/xml_libxml2/SmbiosXml.cpp:420: error: 'xmlDocPtr' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:420: error: 'doc' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:420: error: 'xmlDocGetRootElement' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:421: error: 'findElement' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:431: error: 'xmlutils::getNumberFromXmlAttr' cannot be used as a function
libraries/xml_libxml2/SmbiosXml.cpp:433: error: 'xmlutils::getNumberFromXmlAttr' cannot be used as a function
libraries/xml_libxml2/SmbiosXml.cpp:434: error: 'xmlutils::getNumberFromXmlAttr' cannot be used as a function
libraries/xml_libxml2/SmbiosXml.cpp: At global scope:
libraries/xml_libxml2/SmbiosXml.cpp:438: error: expected ',' or '...' before '*' token
libraries/xml_libxml2/SmbiosXml.cpp:438: error: ISO C++ forbids declaration of 'xmlNode' with no type
libraries/xml_libxml2/SmbiosXml.cpp: In function 'void smbios::printStructureField(std::ostream&, int)':
libraries/xml_libxml2/SmbiosXml.cpp:443: error: 'node' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:452: error: 'item' was not declared in this scope
libraries/xml_libxml2/SmbiosXml.cpp:464: error: 'item' was not declared in this scope
make[1]: *** [libraries/xml_libxml2/libraries_libsmbiosxml_la-SmbiosXml.lo] Fout 1
make[1]: Map '/home/timo/libsmbios-0.13.8' wordt verlaten
make: *** [all-recursive] Fout 1
 
```

so it doesn't even come to make install...
someone who got an answer for this?

---

### Post by dmarsh on 2007-08-02
Works for me on Feisty- perhaps you need some additional -dev packages installed?  From the error messages, you might try installing libxml2-dev as a start, if you don't have it installed already.  If you just can't get it compiled, I can probably temporarily host a pre-compiled directory on my website if you need it...

BTW, the binary you're looking for is dellLEDCtl, and it controls all the LEDs properly except for the one in the touchpad- it doesn't seem to be able to turn it either on or off.  I haven't pursued it much, as I was just looking for a way to control the main LEDs as status indicators, etc.

---

### Post by Nunslaughter on 2007-08-02
hey, i installed that package and it got a little further....


i tried to follow this: 

```
./configure && make && sudo make all
sudo modprobe dcdbas
sudo bins/dellLEDCtl -h
sudo bins/dellLEDCtl -i
sudo bins/dellLEDCtl -z1 1 -z2 2 -z3 2 -l 7 
```

so now make and make all works but then bins/dellLEDCtl - h doesnt:

sudo: bins/dellLEDCtl: command not found

so what do i need to do to get this working?

---

### Post by dmarsh on 2007-08-02
You're nearly there- the dellLEDCtl binary lives in the bin-unsupported directory, rather than the bin-supported directory.  If you've done a 'make install', it will have installed to the /usr/local/bin directory unless you specified somewhere else when running ./configure.

---

### Post by Nunslaughter on 2007-08-02
i didn't change anything when i did ./configure...and the only dellLEDCtl files i can find are in the libsmbios folder which i had already from the beginning (the extracted tar.gz)

these files are dellLEDCtl, dellLEDCtl.cpp ,dellLEDCtl.o

no idea what to do with them or if these are even the right files...

but i don't know if sudo make all worked properly, it said (maybe something different, i'm translating this from dutch)

```
make[1]: Entering folder '/home/timo/libsmbios-0.13.8'
make[1]: Nothing has to be done for 'all-am'.
make[1]: Leaving map '/home/timo/libsmbios-0.13.8'
 
```

thats all it said

---

### Post by dmarsh on 2007-08-02
Looks like you've forgotten the 'make install' step at the end of the build.  The dellLEDCtl file (no extension) is the program that you want, so you should be able to run it directly from the libsmbios build directory to test it.  After you run 'sudo make install', the programs should be in /usr/local/bin.

---

### Post by Nunslaughter on 2007-08-03
yes indeed, now these files are in /usr/local/bin

but now, how can i run this?

sorry for the (maybe) stupid questions...

---

### Post by dmarsh on 2007-08-03
From a terminal window, you can run it with a commandline like this:

sudo /usr/local/bin/dellLEDCtl -z2 4 -l 7

Once you've made sure that it's running, you can explore the other options with:

sudo /usr/local/bin/dellLEDCtl -h

---

### Post by Nunslaughter on 2007-08-03
it works! thanks for your help and explanation!

someone should write a program or something for these leds...

---

