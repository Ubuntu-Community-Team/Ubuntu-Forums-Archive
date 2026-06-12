---
title: "Help with compiling linux version of Fanwor"
date: 2017-04-16
forum: Gaming &amp; Leisure
---

### Post by jg1982 on 2017-04-16
Can some one please help me out? What am i doing wrong?
Would anyone be willing to compile a 32 bit linux version of this game, or be able to tell where i could find a precompiled release of this for linux?
(I have also emailed the author, but as of yet have not got a reply...)

I have download Fanwor from [here]("http://fanwor.tuxfamily.org/files/fanwor-1.14.tar.gz") but can not seem to get it to compile.
I am running Ubuntu mate 16.04 32 bit.
I downloaded the game plus zlib from [here]("http://www.zlib.net/zlib-1.2.11.tar.gz") and libpng from [here]("http://prdownloads.sourceforge.net/libpng/libpng-1.6.29.tar.gz?download") all to the same folder.
I extracted them all to seperate subfolders.
I entered the zlib folder in a terminal and ran the following:
./configure
make
sudo make install

Terminal output:
```
$:~/Desktop/fanwor/zlib-1.2.11$ ./configure
Checking for gcc...
Checking for shared library support...
Building shared library libz.so.1.2.11 with gcc.
Checking for size_t... Yes.
Checking for off64_t... Yes.
Checking for fseeko... Yes.
Checking for strerror... Yes.
Checking for unistd.h... Yes.
Checking for stdarg.h... Yes.
Checking whether to use vs[n]printf() or s[n]printf()... using vs[n]printf().
Checking for vsnprintf() in stdio.h... Yes.
Checking for return value of vsnprintf()... Yes.
Checking for attribute(visibility) support... Yes.
$:~/Desktop/fanwor/zlib-1.2.11$ make
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN -I. -c -o example.o test/example.c
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -c -o adler32.o adler32.c
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -c -o crc32.o crc32.c
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -c -o deflate.o deflate.c
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -c -o infback.o infback.c
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -c -o inffast.o inffast.c
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -c -o inflate.o inflate.c
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -c -o inftrees.o inftrees.c
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -c -o trees.o trees.c
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -c -o zutil.o zutil.c
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -c -o compress.o compress.c
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -c -o uncompr.o uncompr.c
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -c -o gzclose.o gzclose.c
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -c -o gzlib.o gzlib.c
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -c -o gzread.o gzread.c
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -c -o gzwrite.o gzwrite.c
ar rc libz.a adler32.o crc32.o deflate.o infback.o inffast.o inflate.o inftrees.o trees.o zutil.o compress.o uncompr.o gzclose.o gzlib.o gzread.o gzwrite.o 
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN -o example example.o -L. libz.a
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN -I. -c -o minigzip.o test/minigzip.c
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN -o minigzip minigzip.o -L. libz.a
gcc -O3 -fPIC -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -DPIC -c -o objs/adler32.o adler32.c
gcc -O3 -fPIC -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -DPIC -c -o objs/crc32.o crc32.c
gcc -O3 -fPIC -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -DPIC -c -o objs/deflate.o deflate.c
gcc -O3 -fPIC -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -DPIC -c -o objs/infback.o infback.c
gcc -O3 -fPIC -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -DPIC -c -o objs/inffast.o inffast.c
gcc -O3 -fPIC -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -DPIC -c -o objs/inflate.o inflate.c
gcc -O3 -fPIC -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -DPIC -c -o objs/inftrees.o inftrees.c
gcc -O3 -fPIC -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -DPIC -c -o objs/trees.o trees.c
gcc -O3 -fPIC -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -DPIC -c -o objs/zutil.o zutil.c
gcc -O3 -fPIC -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -DPIC -c -o objs/compress.o compress.c
gcc -O3 -fPIC -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -DPIC -c -o objs/uncompr.o uncompr.c
gcc -O3 -fPIC -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -DPIC -c -o objs/gzclose.o gzclose.c
gcc -O3 -fPIC -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -DPIC -c -o objs/gzlib.o gzlib.c
gcc -O3 -fPIC -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -DPIC -c -o objs/gzread.o gzread.c
gcc -O3 -fPIC -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN  -DPIC -c -o objs/gzwrite.o gzwrite.c
gcc -shared -Wl,-soname,libz.so.1,--version-script,zlib.map -O3 -fPIC -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN -o libz.so.1.2.11 adler32.lo crc32.lo deflate.lo infback.lo inffast.lo inflate.lo inftrees.lo trees.lo zutil.lo compress.lo uncompr.lo gzclose.lo gzlib.lo gzread.lo gzwrite.lo  -lc 
rm -f libz.so libz.so.1
ln -s libz.so.1.2.11 libz.so
ln -s libz.so.1.2.11 libz.so.1
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN -o examplesh example.o -L. libz.so.1.2.11
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN -o minigzipsh minigzip.o -L. libz.so.1.2.11
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN -I. -D_FILE_OFFSET_BITS=64 -c -o example64.o test/example.c
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN -o example64 example64.o -L. libz.a
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN -I. -D_FILE_OFFSET_BITS=64 -c -o minigzip64.o test/minigzip.c
gcc -O3 -D_LARGEFILE64_SOURCE=1 -DHAVE_HIDDEN -o minigzip64 minigzip64.o -L. libz.a
$:~/Desktop/fanwor/zlib-1.2.11$ sudo make install
[sudo] password for a: 
rm -f /usr/local/lib/libz.a
cp libz.a /usr/local/lib
chmod 644 /usr/local/lib/libz.a
cp libz.so.1.2.11 /usr/local/lib
chmod 755 /usr/local/lib/libz.so.1.2.11
rm -f /usr/local/share/man/man3/zlib.3
cp zlib.3 /usr/local/share/man/man3
chmod 644 /usr/local/share/man/man3/zlib.3
rm -f /usr/local/lib/pkgconfig/zlib.pc
cp zlib.pc /usr/local/lib/pkgconfig
chmod 644 /usr/local/lib/pkgconfig/zlib.pc
rm -f /usr/local/include/zlib.h /usr/local/include/zconf.h
cp zlib.h zconf.h /usr/local/include
chmod 644 /usr/local/include/zlib.h /usr/local/include/zconf.h
```

I then entered the libpng folder in a terminal and ran the following:
./configure
cmake "."
make
sudo make install

Terminal output:
```
$:~/Desktop/fanwor/libpng-1.6.29$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking how to print strings... printf
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking how to run the C preprocessor... gcc -E
checking for gawk... (cached) gawk
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking the maximum length of command line arguments... 1572864
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for a working dd... /bin/dd
checking how to truncate binary pipes... /bin/dd bs=4096 count=1
checking for mt... mt
checking if mt is a manifest tool... no
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
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking that AWK works... ok
checking if we need to force back C standard to C89... no
checking for ANSI C header files... (cached) yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for C/C++ restrict keyword... __restrict
checking for working strtod... yes
checking for memset... yes
checking for pow... no
checking for pow in -lm... yes
checking for clock_gettime... yes
checking for zlibVersion in -lz... yes
checking for feenableexcept in -lm... yes
checking for feenableexcept... yes
checking if using Solaris linker... no
checking if libraries can be versioned... yes
checking for symbol prefix... 
configure: pkgconfig directory is ${libdir}/pkgconfig
configure: Extra options for compiler: 
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating libpng.pc
config.status: creating libpng-config
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands
$:~/Desktop/fanwor/libpng-1.6.29$ cmake "."
-- The C compiler identification is GNU 5.4.1
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Found ZLIB: /usr/local/lib/libz.so (found version "1.2.11") 
-- Performing Test HAVE_LD_VERSION_SCRIPT
-- Performing Test HAVE_LD_VERSION_SCRIPT - Success
-- Symbol prefix: 
CMake Warning (dev) at CMakeLists.txt:807 (get_target_property):
  Policy CMP0026 is not set: Disallow use of the LOCATION target property.
  Run "cmake --help-policy CMP0026" for policy details.  Use the cmake_policy
  command to set the policy and suppress this warning.

  The LOCATION property should not be read from target "png".  Use the target
  name directly with add_custom_command, or use the generator expression
  $<TARGET_FILE>, as appropriate.

This warning is for project developers.  Use -Wno-dev to suppress it.

CMake Warning (dev) at CMakeLists.txt:816 (get_target_property):
  Policy CMP0026 is not set: Disallow use of the LOCATION target property.
  Run "cmake --help-policy CMP0026" for policy details.  Use the cmake_policy
  command to set the policy and suppress this warning.

  The LOCATION property should not be read from target "png_static".  Use the
  target name directly with add_custom_command, or use the generator
  expression $<TARGET_FILE>, as appropriate.

This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring done
-- Generating done
-- Build files have been written to: /home/a/Desktop/fanwor/libpng-1.6.29
$:~/Desktop/fanwor/libpng-1.6.29$ make
Scanning dependencies of target genfiles
[  1%] Generating pnglibconf.c
[  2%] Generating pnglibconf.out
[  4%] Generating pnglibconf.h
[  5%] Generating scripts/sym.out
[  7%] Generating libpng.sym
[  8%] Generating scripts/vers.out
[ 10%] Generating libpng.vers
[ 11%] Generating pngprefix.h
[ 13%] Generating scripts/intprefix.out
[ 14%] Generating scripts/pnglibconf.c
[ 16%] Generating scripts/prefix.out
[ 17%] Generating scripts/symbols.out
[ 19%] Generating scripts/symbols.chk
[ 19%] Built target genfiles
Scanning dependencies of target png
[ 20%] Building C object CMakeFiles/png.dir/png.c.o
[ 22%] Building C object CMakeFiles/png.dir/pngerror.c.o
[ 23%] Building C object CMakeFiles/png.dir/pngget.c.o
[ 25%] Building C object CMakeFiles/png.dir/pngmem.c.o
[ 26%] Building C object CMakeFiles/png.dir/pngpread.c.o
[ 28%] Building C object CMakeFiles/png.dir/pngread.c.o
[ 29%] Building C object CMakeFiles/png.dir/pngrio.c.o
[ 31%] Building C object CMakeFiles/png.dir/pngrtran.c.o
[ 32%] Building C object CMakeFiles/png.dir/pngrutil.c.o
[ 34%] Building C object CMakeFiles/png.dir/pngset.c.o
[ 35%] Building C object CMakeFiles/png.dir/pngtrans.c.o
[ 37%] Building C object CMakeFiles/png.dir/pngwio.c.o
[ 38%] Building C object CMakeFiles/png.dir/pngwrite.c.o
[ 40%] Building C object CMakeFiles/png.dir/pngwtran.c.o
[ 41%] Building C object CMakeFiles/png.dir/pngwutil.c.o
[ 43%] Linking C shared library libpng16.so
[ 49%] Built target png
Scanning dependencies of target pngimage
[ 50%] Building C object CMakeFiles/pngimage.dir/contrib/libtests/pngimage.c.o
[ 52%] Linking C executable pngimage
[ 52%] Built target pngimage
Scanning dependencies of target png-fix-itxt
[ 53%] Building C object CMakeFiles/png-fix-itxt.dir/contrib/tools/png-fix-itxt.c.o
[ 55%] Linking C executable png-fix-itxt
[ 55%] Built target png-fix-itxt
Scanning dependencies of target pngtest
[ 56%] Building C object CMakeFiles/pngtest.dir/pngtest.c.o
[ 58%] Linking C executable pngtest
[ 58%] Built target pngtest
Scanning dependencies of target pngstest
[ 59%] Building C object CMakeFiles/pngstest.dir/contrib/libtests/pngstest.c.o
[ 61%] Linking C executable pngstest
[ 61%] Built target pngstest
Scanning dependencies of target pngunknown
[ 62%] Building C object CMakeFiles/pngunknown.dir/contrib/libtests/pngunknown.c.o
[ 64%] Linking C executable pngunknown
[ 64%] Built target pngunknown
Scanning dependencies of target png_static
[ 65%] Building C object CMakeFiles/png_static.dir/png.c.o
[ 67%] Building C object CMakeFiles/png_static.dir/pngerror.c.o
[ 68%] Building C object CMakeFiles/png_static.dir/pngget.c.o
[ 70%] Building C object CMakeFiles/png_static.dir/pngmem.c.o
[ 71%] Building C object CMakeFiles/png_static.dir/pngpread.c.o
[ 73%] Building C object CMakeFiles/png_static.dir/pngread.c.o
[ 74%] Building C object CMakeFiles/png_static.dir/pngrio.c.o
[ 76%] Building C object CMakeFiles/png_static.dir/pngrtran.c.o
[ 77%] Building C object CMakeFiles/png_static.dir/pngrutil.c.o
[ 79%] Building C object CMakeFiles/png_static.dir/pngset.c.o
[ 80%] Building C object CMakeFiles/png_static.dir/pngtrans.c.o
[ 82%] Building C object CMakeFiles/png_static.dir/pngwio.c.o
[ 83%] Building C object CMakeFiles/png_static.dir/pngwrite.c.o
[ 85%] Building C object CMakeFiles/png_static.dir/pngwtran.c.o
[ 86%] Building C object CMakeFiles/png_static.dir/pngwutil.c.o
[ 88%] Linking C static library libpng16.a
[ 94%] Built target png_static
Scanning dependencies of target pngfix
[ 95%] Building C object CMakeFiles/pngfix.dir/contrib/tools/pngfix.c.o
[ 97%] Linking C executable pngfix
[ 97%] Built target pngfix
Scanning dependencies of target pngvalid
[ 98%] Building C object CMakeFiles/pngvalid.dir/contrib/libtests/pngvalid.c.o
[100%] Linking C executable pngvalid
[100%] Built target pngvalid
$:~/Desktop/fanwor/libpng-1.6.29$ sudo make install
[sudo] password for a: 
[ 19%] Built target genfiles
[ 49%] Built target png
[ 52%] Built target pngimage
[ 55%] Built target png-fix-itxt
[ 58%] Built target pngtest
[ 61%] Built target pngstest
[ 64%] Built target pngunknown
[ 94%] Built target png_static
[ 97%] Built target pngfix
[100%] Built target pngvalid
Install the project...
-- Install configuration: ""
-- Installing: /usr/local/lib/libpng16.so.16.29.0
-- Installing: /usr/local/lib/libpng16.so.16
-- Installing: /usr/local/lib/libpng16.so
-- Set runtime path of "/usr/local/lib/libpng16.so.16.29.0" to ""
-- Installing: /usr/local/lib/libpng16.a
-- Installing: /usr/local/lib/libpng.so
-- Installing: /usr/local/lib/libpng.a
-- Installing: /usr/local/include/png.h
-- Installing: /usr/local/include/pngconf.h
-- Installing: /usr/local/include/pnglibconf.h
-- Installing: /usr/local/include/libpng16/png.h
-- Installing: /usr/local/include/libpng16/pngconf.h
-- Installing: /usr/local/include/libpng16/pnglibconf.h
-- Installing: /usr/local/bin/libpng-config
-- Installing: /usr/local/bin/libpng16-config
-- Installing: /usr/local/bin/pngfix
-- Set runtime path of "/usr/local/bin/pngfix" to ""
-- Installing: /usr/local/bin/png-fix-itxt
-- Set runtime path of "/usr/local/bin/png-fix-itxt" to ""
-- Installing: /usr/local/share/man/man3/libpng.3
-- Installing: /usr/local/share/man/man3/libpngpf.3
-- Installing: /usr/local/share/man/man5/png.5
-- Installing: /usr/local/lib/pkgconfig/libpng.pc
-- Up-to-date: /usr/local/bin/libpng-config
-- Installing: /usr/local/lib/pkgconfig/libpng16.pc
-- Up-to-date: /usr/local/bin/libpng16-config
-- Installing: /usr/local/lib/libpng/libpng16.cmake
-- Installing: /usr/local/lib/libpng/libpng16-noconfig.cmake
```

Then i entered into the fanwor folder in a terminal and ran make.

Terminal output:
```
$:~/Desktop/fanwor/fanwor-1.14$ export LD_LIBRARY_PATH="/usr/local/lib/"
$:~/Desktop/fanwor/fanwor-1.14$ make
make -C src
make[1]: Entering directory '/home/a/Desktop/fanwor/fanwor-1.14/src'
cc -I. -I./arch/sdl -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DWITH_SOUND -g -O2 -Wall -Wmissing-prototypes -Wstrict-prototypes   -c -o fwdisk.o fwdisk.c
cc -I. -I./arch/sdl -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DWITH_SOUND -g -O2 -Wall -Wmissing-prototypes -Wstrict-prototypes   -c -o fwfight.o fwfight.c
cc -I. -I./arch/sdl -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DWITH_SOUND -g -O2 -Wall -Wmissing-prototypes -Wstrict-prototypes   -c -o fwreact.o fwreact.c
cc -I. -I./arch/sdl -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DWITH_SOUND -g -O2 -Wall -Wmissing-prototypes -Wstrict-prototypes   -c -o fwmain.o fwmain.c
cc -I. -I./arch/sdl -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DWITH_SOUND -g -O2 -Wall -Wmissing-prototypes -Wstrict-prototypes   -c -o fwdata.o fwdata.c
cc -I. -I./arch/sdl -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DWITH_SOUND -g -O2 -Wall -Wmissing-prototypes -Wstrict-prototypes   -c -o arch/sdl/fwguiini.o arch/sdl/fwguiini.c
cc -I. -I./arch/sdl -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DWITH_SOUND -g -O2 -Wall -Wmissing-prototypes -Wstrict-prototypes   -c -o arch/sdl/fwgui.o arch/sdl/fwgui.c
cc -I. -I./arch/sdl -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DWITH_SOUND -g -O2 -Wall -Wmissing-prototypes -Wstrict-prototypes   -c -o arch/sdl/fwgraf.o arch/sdl/fwgraf.c
cc -I. -I./arch/sdl -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DWITH_SOUND -g -O2 -Wall -Wmissing-prototypes -Wstrict-prototypes   -c -o arch/sdl/fwmusic.o arch/sdl/fwmusic.c
cc -I. -I./arch/sdl -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DWITH_SOUND -g -O2 -Wall -Wmissing-prototypes -Wstrict-prototypes   -c -o arch/sdl/loadpng.o arch/sdl/loadpng.c
cc fwdisk.o fwfight.o fwreact.o fwmain.o fwdata.o ./arch/sdl/fwguiini.o ./arch/sdl/fwgui.o ./arch/sdl/fwgraf.o ./arch/sdl/fwmusic.o ./arch/sdl/loadpng.o -lpng -L/usr/lib/i386-linux-gnu -lSDL -lz -lSDL_mixer -o../fanwor
./arch/sdl/loadpng.o: In function `LoadPNG':
/home/a/Desktop/fanwor/fanwor-1.14/src/arch/sdl/loadpng.c:134: undefined reference to `png_set_longjmp_fn'
/home/a/Desktop/fanwor/fanwor-1.14/src/arch/sdl/loadpng.c:248: undefined reference to `png_get_palette_max'
collect2: error: ld returned 1 exit status
Makefile:38: recipe for target 'fanwor' failed
make[1]: *** [fanwor] Error 1
make[1]: Leaving directory '/home/a/Desktop/fanwor/fanwor-1.14/src'
Makefile:3: recipe for target 'all' failed
make: *** [all] Error 2
```

---

### Post by jg1982 on 2017-04-16
The author has responded to my email, and has told me to install libpng-dev.
This is already installed (libpng12-dev). The zlib dependency seems to be provided by zlib1g and zlib1g-dev (which are both installed).

---

### Post by jg1982 on 2017-04-23
The latest (1.15,) release of this game on the authors git appears to compile without issue.

---

