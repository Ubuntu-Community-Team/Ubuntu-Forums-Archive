---
title: "Compiling PCSX 0.9.2 RC2 problems"
date: 2006-12-05
forum: Gaming &amp; Leisure
---

### Post by damvcoool on 2006-12-05
I'm Have some trouble making this.

I execute
aclocal
autoconf
automake-1.9
./configure --enable-devbuild
make

and i get an error :'(

```

/media/hda3/PCSX2_0.9.2_Source.7z_FILES$ aclocal ; autoconf ; automake-1.9 ; ./configure --enable-devbuild ; make
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build... yes
checking for a x86-64 CPU... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating DebugTools/Makefile
config.status: creating Linux/Makefile
config.status: creating IPU/Makefile
config.status: creating IPU/mpeg2lib/Makefile
config.status: creating pcl/Makefile
config.status: creating RDebug/Makefile
config.status: creating tinyxml/Makefile
config.status: creating x86/Makefile
config.status: creating x86/ix86/Makefile
config.status: creating x86/ix86-32/Makefile
config.status: creating x86/ix86-64/Makefile
config.status: creating zlib/Makefile
config.status: executing depfiles commands
./configure: line 5491: bindir: command not found
Configuration:
  Target system type:    
  x86-64 build?        no
  Debug build?         no
  Dev build?           yes
Making all in .
make[1]: Entering directory `/media/hda3/PCSX2_0.9.2_Source.7z_FILES'
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.2\" -DPACKAGE_STRING=\"pcsx2\ 0.9.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.2\" -DPCSX2_DEVBUILD=1 -I. -I. -IDebugTools/ -Ix86/  -O2 -fomit-frame-pointer   -O2 -fomit-frame-pointer  -MT CdRom.o -MD -MP -MF ".deps/CdRom.Tpo" -c -o CdRom.o CdRom.c; \
        then mv -f ".deps/CdRom.Tpo" ".deps/CdRom.Po"; else rm -f ".deps/CdRom.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.2\" -DPACKAGE_STRING=\"pcsx2\ 0.9.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.2\" -DPCSX2_DEVBUILD=1 -I. -I. -IDebugTools/ -Ix86/  -O2 -fomit-frame-pointer   -O2 -fomit-frame-pointer  -MT R3000A.o -MD -MP -MF ".deps/R3000A.Tpo" -c -o R3000A.o R3000A.c; \
        then mv -f ".deps/R3000A.Tpo" ".deps/R3000A.Po"; else rm -f ".deps/R3000A.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.2\" -DPACKAGE_STRING=\"pcsx2\ 0.9.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.2\" -DPCSX2_DEVBUILD=1 -I. -I. -IDebugTools/ -Ix86/  -O2 -fomit-frame-pointer   -O2 -fomit-frame-pointer  -MT memcpy_amd.o -MD -MP -MF ".deps/memcpy_amd.Tpo" -c -o memcpy_amd.o memcpy_amd.cpp; \
        then mv -f ".deps/memcpy_amd.Tpo" ".deps/memcpy_amd.Po"; else rm -f ".deps/memcpy_amd.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.2\" -DPACKAGE_STRING=\"pcsx2\ 0.9.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.2\" -DPCSX2_DEVBUILD=1 -I. -I. -IDebugTools/ -Ix86/  -O2 -fomit-frame-pointer   -O2 -fomit-frame-pointer  -MT VU0.o -MD -MP -MF ".deps/VU0.Tpo" -c -o VU0.o VU0.c; \
        then mv -f ".deps/VU0.Tpo" ".deps/VU0.Po"; else rm -f ".deps/VU0.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.2\" -DPACKAGE_STRING=\"pcsx2\ 0.9.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.2\" -DPCSX2_DEVBUILD=1 -I. -I. -IDebugTools/ -Ix86/  -O2 -fomit-frame-pointer   -O2 -fomit-frame-pointer  -MT CDVD.o -MD -MP -MF ".deps/CDVD.Tpo" -c -o CDVD.o CDVD.c; \
        then mv -f ".deps/CDVD.Tpo" ".deps/CDVD.Po"; else rm -f ".deps/CDVD.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.2\" -DPACKAGE_STRING=\"pcsx2\ 0.9.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.2\" -DPCSX2_DEVBUILD=1 -I. -I. -IDebugTools/ -Ix86/  -O2 -fomit-frame-pointer   -O2 -fomit-frame-pointer  -MT Elfheader.o -MD -MP -MF ".deps/Elfheader.Tpo" -c -o Elfheader.o Elfheader.c; \
        then mv -f ".deps/Elfheader.Tpo" ".deps/Elfheader.Po"; else rm -f ".deps/Elfheader.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.2\" -DPACKAGE_STRING=\"pcsx2\ 0.9.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.2\" -DPCSX2_DEVBUILD=1 -I. -I. -IDebugTools/ -Ix86/  -O2 -fomit-frame-pointer   -O2 -fomit-frame-pointer  -MT Memory.o -MD -MP -MF ".deps/Memory.Tpo" -c -o Memory.o Memory.c; \
        then mv -f ".deps/Memory.Tpo" ".deps/Memory.Po"; else rm -f ".deps/Memory.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.2\" -DPACKAGE_STRING=\"pcsx2\ 0.9.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.2\" -DPCSX2_DEVBUILD=1 -I. -I. -IDebugTools/ -Ix86/  -O2 -fomit-frame-pointer   -O2 -fomit-frame-pointer  -MT PsxCounters.o -MD -MP -MF ".deps/PsxCounters.Tpo" -c -o PsxCounters.o PsxCounters.c; \
        then mv -f ".deps/PsxCounters.Tpo" ".deps/PsxCounters.Po"; else rm -f ".deps/PsxCounters.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.2\" -DPACKAGE_STRING=\"pcsx2\ 0.9.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.2\" -DPCSX2_DEVBUILD=1 -I. -I. -IDebugTools/ -Ix86/  -O2 -fomit-frame-pointer   -O2 -fomit-frame-pointer  -MT R5900.o -MD -MP -MF ".deps/R5900.Tpo" -c -o R5900.o R5900.c; \
        then mv -f ".deps/R5900.Tpo" ".deps/R5900.Po"; else rm -f ".deps/R5900.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.2\" -DPACKAGE_STRING=\"pcsx2\ 0.9.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.2\" -DPCSX2_DEVBUILD=1 -I. -I. -IDebugTools/ -Ix86/  -O2 -fomit-frame-pointer   -O2 -fomit-frame-pointer  -MT VU0micro.o -MD -MP -MF ".deps/VU0micro.Tpo" -c -o VU0micro.o VU0micro.c; \
        then mv -f ".deps/VU0micro.Tpo" ".deps/VU0micro.Po"; else rm -f ".deps/VU0micro.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.2\" -DPACKAGE_STRING=\"pcsx2\ 0.9.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.2\" -DPCSX2_DEVBUILD=1 -I. -I. -IDebugTools/ -Ix86/  -O2 -fomit-frame-pointer   -O2 -fomit-frame-pointer  -MT CDVDiso.o -MD -MP -MF ".deps/CDVDiso.Tpo" -c -o CDVDiso.o CDVDiso.c; \
        then mv -f ".deps/CDVDiso.Tpo" ".deps/CDVDiso.Po"; else rm -f ".deps/CDVDiso.Tpo"; exit 1; fi
CDVDiso.c: In function ‘DvdRead’:
CDVDiso.c:202: error: invalid lvalue in assignment
CDVDiso.c: In function ‘CDVD_findfile’:
CDVDiso.c:304: error: invalid lvalue in assignment
CDVDiso.c:309: error: invalid lvalue in assignment
CDVDiso.c:310: error: invalid lvalue in assignment
CDVDiso.c:364: error: invalid lvalue in assignment
CDVDiso.c:389: error: invalid lvalue in assignment
CDVDiso.c:414: error: invalid lvalue in assignment
CDVDiso.c:415: error: invalid lvalue in assignment
CDVDiso.c:416: error: invalid lvalue in assignment
CDVDiso.c:423: error: invalid lvalue in assignment
CDVDiso.c:428: error: invalid lvalue in assignment
CDVDiso.c:429: error: invalid lvalue in assignment
CDVDiso.c:430: error: invalid lvalue in assignment
CDVDiso.c:459: error: invalid lvalue in assignment
CDVDiso.c:474: error: invalid lvalue in assignment
CDVDiso.c: In function ‘CDVD_GetDir_RPC_request’:
CDVDiso.c:525: error: invalid lvalue in assignment
CDVDiso.c:530: error: invalid lvalue in assignment
CDVDiso.c:531: error: invalid lvalue in assignment
CDVDiso.c:567: error: invalid lvalue in assignment
CDVDiso.c:592: error: invalid lvalue in assignment
CDVDiso.c:615: error: invalid lvalue in assignment
CDVDiso.c:616: error: invalid lvalue in assignment
CDVDiso.c:617: error: invalid lvalue in assignment
CDVDiso.c:629: error: invalid lvalue in assignment
CDVDiso.c:641: error: invalid lvalue in assignment
CDVDiso.c:642: error: invalid lvalue in assignment
CDVDiso.c:643: error: invalid lvalue in assignment
CDVDiso.c:665: error: invalid lvalue in assignment
CDVDiso.c:698: error: invalid lvalue in assignment
CDVDiso.c: In function ‘CDVD_GetDir_RPC_get_entries’:
CDVDiso.c:735: error: invalid lvalue in assignment
CDVDiso.c:736: error: invalid lvalue in assignment
CDVDiso.c:737: error: invalid lvalue in assignment
CDVDiso.c:742: error: invalid lvalue in assignment
CDVDiso.c:767: error: invalid lvalue in assignment
CDVDiso.c:793: error: invalid lvalue in assignment
CDVDiso.c:803: error: invalid lvalue in assignment
CDVDiso.c:809: error: invalid lvalue in assignment
make[1]: *** [CDVDiso.o] Error 1
make[1]: Leaving directory `/media/hda3/PCSX2_0.9.2_Source.7z_FILES'
make: *** [all-recursive] Error 1



```

Can anyone help me please.

I also tried without the  --enable-devbuild flag but i got the same result.

---

### Post by chadk on 2006-12-05
what are you trying to make or build?  PCSX?  You might want to tell us..

---

### Post by damvcoool on 2006-12-06
Sorry, i thought i put it on the tittle :$
Im trying to compile PCSX2 version 0.9.2 RC2

Can someone please Change the title. to:

Compiling PCSX2 0.9.2 RC2 problems

---

### Post by Perfect Storm on 2006-12-06
Done.

---

### Post by dracule on 2006-12-06
it says no command exist for me...
EDIT nvr mnd, but i get this error:
Misc.h: In function &#8216;void* pcsx2_aligned_malloc(size_t, size_t)&#8217;:
Misc.h:157: error: cast from &#8216;char*&#8217; to &#8216;int&#8217; loses precision
make[1]: *** [memcpy_amd.o] Error 1
make[1]: Leaving directory `/home/****/Desktop/PCSX2'
make: *** [all-recursive] Error 1

---

### Post by kazuya on 2006-12-19
I wish I knew the answer to this. Any ideas guys? I am trying to get PCSX2 as well. This is functional for window users already. Not without some difficulty and great system Specs. How do we do that on Ubuntu or linux for that matter?

---

### Post by po0f on 2006-12-19
kazuya,

AFAIK, the PCSX2 devs have pushed back Linux support to a later release.  (It was supposed to be this release, oh well.)

---

### Post by kazuya on 2006-12-20
SOrry. This was the case since linuxapp retired to focus on family affairs. I am glad they would do it for linux as well. Else I would have just gone without it. I would not be getting windows just for emulation. ANy ideas on minimum system spec on linux machine or all machines?

---

### Post by po0f on 2006-12-20
kazuya,

From what I gather, you pretty much need a dual core proc (not listed as a minimum requirement but it should have been) and at *least* a 6xxx series NVIDIA card (IIRC it requires SM2.0).  Most people get an average of 17FPS in game on most games, even with pretty beefy boxes.

---

### Post by kazuya on 2006-12-20
ouch. I give up then. No hope for my system.

---

### Post by damvcoool on 2006-12-21
No hope at least until feb next year when 9.3 is out 
so we can ask PCSX2 to be some what incorporated into feisty and if not at least in the next version :D

---

