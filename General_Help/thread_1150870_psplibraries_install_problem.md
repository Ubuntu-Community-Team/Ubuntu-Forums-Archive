---
title: "psplibraries install problem"
date: 2009-05-06
forum: General Help
---

### Post by 2weird on 2009-05-06
I have successfully installed the psptoolchain on Ubuntu (jaunty) and I wanted to install the psplibraries but I get the following error: 
```

At revision 2458.
rm -f libz.a  adler32.o compress.o crc32.o gzio.o uncompr.o deflate.o trees.o zutil.o inflate.o infback.o inftrees.o inffast.o PARAM.SFO EBOOT.PBP 
psp-gcc -I. -I/usr/local/pspdev/psp/sdk/include -O2 -G0 -D_PSP_FW_VERSION=150   -c -o adler32.o adler32.c
psp-gcc -I. -I/usr/local/pspdev/psp/sdk/include -O2 -G0 -D_PSP_FW_VERSION=150   -c -o compress.o compress.c
psp-gcc -I. -I/usr/local/pspdev/psp/sdk/include -O2 -G0 -D_PSP_FW_VERSION=150   -c -o crc32.o crc32.c
psp-gcc -I. -I/usr/local/pspdev/psp/sdk/include -O2 -G0 -D_PSP_FW_VERSION=150   -c -o gzio.o gzio.c
psp-gcc -I. -I/usr/local/pspdev/psp/sdk/include -O2 -G0 -D_PSP_FW_VERSION=150   -c -o uncompr.o uncompr.c
psp-gcc -I. -I/usr/local/pspdev/psp/sdk/include -O2 -G0 -D_PSP_FW_VERSION=150   -c -o deflate.o deflate.c
psp-gcc -I. -I/usr/local/pspdev/psp/sdk/include -O2 -G0 -D_PSP_FW_VERSION=150   -c -o trees.o trees.c
psp-gcc -I. -I/usr/local/pspdev/psp/sdk/include -O2 -G0 -D_PSP_FW_VERSION=150   -c -o zutil.o zutil.c
psp-gcc -I. -I/usr/local/pspdev/psp/sdk/include -O2 -G0 -D_PSP_FW_VERSION=150   -c -o inflate.o inflate.c
psp-gcc -I. -I/usr/local/pspdev/psp/sdk/include -O2 -G0 -D_PSP_FW_VERSION=150   -c -o infback.o infback.c
psp-gcc -I. -I/usr/local/pspdev/psp/sdk/include -O2 -G0 -D_PSP_FW_VERSION=150   -c -o inftrees.o inftrees.c
psp-gcc -I. -I/usr/local/pspdev/psp/sdk/include -O2 -G0 -D_PSP_FW_VERSION=150   -c -o inffast.o inffast.c
psp-ar cru libz.a adler32.o compress.o crc32.o gzio.o uncompr.o deflate.o trees.o zutil.o inflate.o infback.o inftrees.o inffast.o
psp-ranlib libz.a
Installing libz into /usr/local/pspdev/psp
Done
rm -f libz.a  adler32.o compress.o crc32.o gzio.o uncompr.o deflate.o trees.o zutil.o inflate.o infback.o inftrees.o inffast.o PARAM.SFO EBOOT.PBP 
At revision 2458.
rm -f *.o libbz2.a
psp-gcc -Wall -Winline -O2 -G0 -D_FILE_OFFSET_BITS=64 -c blocksort.c
psp-gcc -Wall -Winline -O2 -G0 -D_FILE_OFFSET_BITS=64 -c huffman.c
psp-gcc -Wall -Winline -O2 -G0 -D_FILE_OFFSET_BITS=64 -c crctable.c
psp-gcc -Wall -Winline -O2 -G0 -D_FILE_OFFSET_BITS=64 -c randtable.c
psp-gcc -Wall -Winline -O2 -G0 -D_FILE_OFFSET_BITS=64 -c compress.c
compress.c: In function ‘BZ2_compressBlock’:
compress.c:74: warning: inlining failed in call to ‘bsW’: call is unlikely and code size would grow
compress.c:519: warning: called from here
compress.c:74: warning: inlining failed in call to ‘bsW’: call is unlikely and code size would grow
compress.c:520: warning: called from here
psp-gcc -Wall -Winline -O2 -G0 -D_FILE_OFFSET_BITS=64 -c decompress.c
psp-gcc -Wall -Winline -O2 -G0 -D_FILE_OFFSET_BITS=64 -c bzlib.c
rm -f libbz2.a
psp-ar cq libbz2.a blocksort.o huffman.o crctable.o randtable.o compress.o decompress.o bzlib.o
psp-ranlib libbz2.a
if ( test ! -d /usr/local/pspdev/psp/lib ) ; then mkdir -p /usr/local/pspdev/psp/lib ; fi
if ( test ! -d /usr/local/pspdev/psp/include ) ; then mkdir -p /usr/local/pspdev/psp/include ; fi
cp -f bzlib.h /usr/local/pspdev/psp/include
chmod a+r /usr/local/pspdev/psp/include/bzlib.h
cp -f libbz2.a /usr/local/pspdev/psp/lib
chmod a+r /usr/local/pspdev/psp/lib/libbz2.a
rm -f *.o libbz2.a
At revision 2458.
running `aclocal -I .'
running `libtoolize --copy'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
running `autoconf'
cd builds/unix; ./configure --host psp --prefix=/usr/local/pspdev/psp
configure: WARNING: If you wanted to set the --build type, don't use --host.
    If a cross compiler is detected then cross compile mode will be used.
checking build system type... /bin/bash: ./config.guess: No such file or directory
configure: error: cannot guess build type; you must specify one
make: *** [builds/unix/unix-def.mk] Error 1
../scripts/003-freetype.sh: Failed.
ERROR: Could not run the libraries script.

```

A little bit near the end you can see that it can not find config.guess.
What is config.guess and where can I find it (if that truly is the problem) and if not how can I fix this problem?

Thanks in advance.

---

