---
title: "Mednafen libsndfile not found error"
date: 2013-01-05
forum: Gaming &amp; Leisure
---

### Post by bobayoga on 2013-01-05
Hi! I'm trying to install the latest version of mednafen (0.9.26). I got an error about OpenGL, and I fixed it. Then I got an error about SDL and I fixed that as well. Now this is what I get:

```
~/Documents/mednafen/mednafen$ ./configure
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking how to run the C preprocessor... gcc -E
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
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
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether the -Werror option is usable... yes
checking for simple visibility declarations... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGEFILE_SOURCE value needed for large files... no
checking for ptrdiff_t... yes
checking for size_t... yes
checking size of short... 2
checking size of int... 4
checking size of long... 4
checking size of long long... 8
checking size of double... 8
checking size of __int64... 0
checking size of void *... 4
checking size of size_t... 4
checking size of ptrdiff_t... 4
checking size of off_t... 8
checking for an ANSI C-conforming const... yes
checking for memcmp... yes
checking for memcpy... yes
checking for memmove... yes
checking for memset... yes
checking for mmap... yes
checking for munmap... yes
checking for madvise... yes
checking for signal... yes
checking for sigaction... yes
checking for fcntl... yes
checking for getenv... yes
checking for putenv... yes
checking for setenv... yes
checking for gettimeofday... yes
checking for getpwuid... yes
checking for getuid... yes
checking for nanosleep... yes
checking for usleep... yes
checking for strerror... yes
checking for strerror_r... yes
checking for ftello... yes
checking for fopen64... yes
checking for fseeko64... yes
checking for ftello64... yes
checking for fstat64... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for mkdir... yes
checking for _mkdir... no
checking whether mkdir takes one argument... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for library containing clock_gettime... -lrt
checking for clock_gettime... yes
checking OpenGL/gl.h usability... no
checking OpenGL/gl.h presence... no
checking for OpenGL/gl.h... no
checking for X... libraries , headers 
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking whether we are using the GNU C Library 2 or newer... yes
checking for ranlib... (cached) ranlib
checking for inline... inline
checking for stdint.h... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/param.h... yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether integer division by zero raises SIGFPE... yes
checking for inttypes.h... yes
checking for unsigned long long int... yes
checking for inttypes.h... (cached) yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking whether imported symbols can be declared weak... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pthread_kill in -lpthread... yes
checking for multithread API to use... posix
checking for pthread_rwlock_t... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking for inttypes.h... (cached) yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for unistd.h... (cached) yes
checking for sys/param.h... (cached) yes
checking for getcwd... yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... (cached) yes
checking for mempcpy... yes
checking for munmap... (cached) yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for uselocale... yes
checking for argz_count... yes
checking for argz_stringify... yes
checking for argz_next... yes
checking for __fsetlocking... yes
checking whether feof_unlocked is declared... yes
checking whether fgets_unlocked is declared... yes
checking for bison... no
checking for long long int... yes
checking for wchar_t... yes
checking for wint_t... yes
checking for intmax_t... yes
checking whether printf() supports POSIX/XSI format strings... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking for stdint.h... (cached) yes
checking for SIZE_MAX... (((1U << 31) - 1) * 2 + 1)
checking for stdint.h... (cached) yes
checking for working fcntl.h... yes
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for ptrdiff_t... (cached) yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for asprintf... yes
checking for fwprintf... yes
checking for newlocale... yes
checking for putenv... (cached) yes
checking for setenv... (cached) yes
checking for setlocale... yes
checking for snprintf... yes
checking for strnlen... yes
checking for wcslen... yes
checking for wcsnlen... yes
checking for mbrtowc... yes
checking for wcrtomb... yes
checking whether _snprintf is declared... no
checking whether _snwprintf is declared... no
checking whether getc_unlocked is declared... yes
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for CFPreferencesCopyAppValue... (cached) no
checking for CFLocaleCopyCurrent... (cached) no
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for zlibVersion in -lz... yes
checking OPTIMIZER_FLAGS for gcc -fomit-frame-pointer... -fomit-frame-pointer
checking OPTIMIZER_FLAGS for gcc -finline-limit=6000... -finline-limit=6000
checking OPTIMIZER_FLAGS for gcc --param large-function-growth=800... --param large-function-growth=800
checking OPTIMIZER_FLAGS for gcc --param inline-unit-growth=175... --param inline-unit-growth=175
checking OPTIMIZER_FLAGS for gcc --param max-inline-insns-single=10000... --param max-inline-insns-single=10000
checking for compiler flags to disable strict overflow... -fno-strict-overflow
checking WARNING_FLAGS for gcc -Wall... -Wall
checking WARNING_FLAGS for gcc -Winline... -Winline
checking WARNING_FLAGS for gcc -Wshadow... -Wshadow
checking WARNING_FLAGS for gcc -Wempty-body... -Wempty-body
checking WARNING_FLAGS for gcc -Wignored-qualifiers... -Wignored-qualifiers
checking SNES_EXTRA_FLAGS for gcc -Wno-unused... -Wno-unused
checking SNES_EXTRA_FLAGS for gcc -Wno-inline... -Wno-inline
checking SNES_EXTRA_FLAGS for gcc -Wno-shadow... -Wno-shadow
checking SNES_EXTRA_FLAGS for gcc -Wno-sign-compare... -Wno-sign-compare
checking SNES_EXTRA_FLAGS for gcc -Wno-inline... (cached) -Wno-inline
checking SNES_EXTRA_FLAGS for gcc -Wno-ignored-qualifiers... -Wno-ignored-qualifiers
checking SNES_EXTRA_FLAGS for gcc -Wno-inline... (cached) -Wno-inline
checking SNES_EXTRA_FLAGS for gcc -Wno-uninitialized... -Wno-uninitialized
checking SNES_EXTRA_FLAGS for gcc -Wno-parentheses... -Wno-parentheses
checking SNES_EXTRA_FLAGS for gcc -Wno-switch... -Wno-switch
checking GBA_EXTRA_FLAGS for gcc -fno-unit-at-a-time... -fno-unit-at-a-time
checking MDFN_COMPAT_FLAGS for gcc -fsigned-char... -fsigned-char
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.0... found.
checking for snd_ctl_open in -lasound... yes
checking for JACK... no
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for LIBCDIO... yes
checking for SNDFILE... no
configure: error: *** libsndfile >= 1.0.2 not found!
```

I've been getting this "error: *** libsndfile >= 1.0.2 not found!" for a while now.

So I tried downloading a file called libsndfile_1.0.21.orig.tar.gz

When I untar it, this is what I get:

```
~$ tar -zxvf /home/joel/Documents/mednafen/libsndfile_1.0.21.orig.tar.gz 
libsndfile-1.0.21/
libsndfile-1.0.21/programs/
libsndfile-1.0.21/programs/test-sndfile-metadata-set.py
libsndfile-1.0.21/programs/sndfile-play-beos.cpp
libsndfile-1.0.21/programs/common.h
libsndfile-1.0.21/programs/sndfile-deinterleave.c
libsndfile-1.0.21/programs/sndfile-metadata-set.c
libsndfile-1.0.21/programs/Makefile.in
libsndfile-1.0.21/programs/sndfile-cmp.c
libsndfile-1.0.21/programs/sndfile-metadata-get.c
libsndfile-1.0.21/programs/sndfile-play.c
libsndfile-1.0.21/programs/sndfile-info.c
libsndfile-1.0.21/programs/sndfile-concat.c
libsndfile-1.0.21/programs/sndfile-interleave.c
libsndfile-1.0.21/programs/common.c
libsndfile-1.0.21/programs/sndfile-convert.c
libsndfile-1.0.21/programs/Makefile.am
libsndfile-1.0.21/build-test-tarball.mk.in
libsndfile-1.0.21/doc/
libsndfile-1.0.21/doc/NEWS
libsndfile-1.0.21/doc/command.html
libsndfile-1.0.21/doc/libsndfile.jpg
libsndfile-1.0.21/doc/octave.html
libsndfile-1.0.21/doc/embedded_files.html
libsndfile-1.0.21/doc/dither.html
libsndfile-1.0.21/doc/AUTHORS
libsndfile-1.0.21/doc/Makefile.in
libsndfile-1.0.21/doc/libsndfile.css
libsndfile-1.0.21/doc/pkgconfig.html
libsndfile-1.0.21/doc/libsndfile.css.in
libsndfile-1.0.21/doc/api.html
libsndfile-1.0.21/doc/ChangeLog
libsndfile-1.0.21/doc/sndfile_info.html
libsndfile-1.0.21/doc/bugs.html
libsndfile-1.0.21/doc/new_file_type.HOWTO
libsndfile-1.0.21/doc/win32.html
libsndfile-1.0.21/doc/index.html
libsndfile-1.0.21/doc/lists.html
libsndfile-1.0.21/doc/Makefile.am
libsndfile-1.0.21/doc/README
libsndfile-1.0.21/doc/FAQ.html
libsndfile-1.0.21/doc/tutorial.html
libsndfile-1.0.21/NEWS
libsndfile-1.0.21/Octave/
libsndfile-1.0.21/Octave/sndfile_load.m
libsndfile-1.0.21/Octave/PKG_ADD
libsndfile-1.0.21/Octave/Makefile.in
libsndfile-1.0.21/Octave/octave_test.sh
libsndfile-1.0.21/Octave/sndfile_play.m
libsndfile-1.0.21/Octave/sndfile.cc
libsndfile-1.0.21/Octave/octave_test.m
libsndfile-1.0.21/Octave/sndfile_save.m
libsndfile-1.0.21/Octave/Makefile.am
libsndfile-1.0.21/M4/
libsndfile-1.0.21/M4/flexible_array.m4
libsndfile-1.0.21/M4/ltversion.m4
libsndfile-1.0.21/M4/add_cflags.m4
libsndfile-1.0.21/M4/libtool.m4
libsndfile-1.0.21/M4/ltoptions.m4
libsndfile-1.0.21/M4/gcc_version.m4
libsndfile-1.0.21/M4/Makefile.in
libsndfile-1.0.21/M4/ltsugar.m4
libsndfile-1.0.21/M4/endian.m4
libsndfile-1.0.21/M4/extra_pkg.m4
libsndfile-1.0.21/M4/octave.m4
libsndfile-1.0.21/M4/llrint.m4
libsndfile-1.0.21/M4/mkoctfile_version.m4
libsndfile-1.0.21/M4/lrint.m4
libsndfile-1.0.21/M4/lt~obsolete.m4
libsndfile-1.0.21/M4/extra_largefile.m4
libsndfile-1.0.21/M4/add_cxxflags.m4
libsndfile-1.0.21/M4/Makefile.am
libsndfile-1.0.21/M4/lrintf.m4
libsndfile-1.0.21/M4/clip_mode.m4
libsndfile-1.0.21/M4/shave.m4
libsndfile-1.0.21/sndfile.pc.in
libsndfile-1.0.21/Win32/
libsndfile-1.0.21/Win32/Makefile.in
libsndfile-1.0.21/Win32/README-precompiled-dll.txt
libsndfile-1.0.21/Win32/testprog.c
libsndfile-1.0.21/Win32/Makefile.am
libsndfile-1.0.21/examples/
libsndfile-1.0.21/examples/sfprocess.c
libsndfile-1.0.21/examples/Makefile.in
libsndfile-1.0.21/examples/make_sine.c
libsndfile-1.0.21/examples/sndfilehandle.cc
libsndfile-1.0.21/examples/generate.c
libsndfile-1.0.21/examples/list_formats.c
libsndfile-1.0.21/examples/Makefile.am
libsndfile-1.0.21/examples/sndfile-to-text.c
libsndfile-1.0.21/AUTHORS
libsndfile-1.0.21/configure
libsndfile-1.0.21/Makefile.in
libsndfile-1.0.21/ChangeLog
libsndfile-1.0.21/man/
libsndfile-1.0.21/man/sndfile-concat.1
libsndfile-1.0.21/man/sndfile-info.1
libsndfile-1.0.21/man/sndfile-play.1
libsndfile-1.0.21/man/Makefile.in
libsndfile-1.0.21/man/sndfile-metadata-get.1
libsndfile-1.0.21/man/sndfile-cmp.1
libsndfile-1.0.21/man/Makefile.am
libsndfile-1.0.21/man/sndfile-convert.1
libsndfile-1.0.21/INSTALL
libsndfile-1.0.21/src/
libsndfile-1.0.21/src/test_conversions.c
libsndfile-1.0.21/src/test_ima_oki_adpcm.c
libsndfile-1.0.21/src/pvf.c
libsndfile-1.0.21/src/ircam.c
libsndfile-1.0.21/src/strings.c
libsndfile-1.0.21/src/config.h.in
libsndfile-1.0.21/src/macos.c
libsndfile-1.0.21/src/ima_adpcm.c
libsndfile-1.0.21/src/common.h
libsndfile-1.0.21/src/mat5.c
libsndfile-1.0.21/src/test_audio_detect.c
libsndfile-1.0.21/src/ima_oki_adpcm.h
libsndfile-1.0.21/src/Symbols.linux
libsndfile-1.0.21/src/create_symbols_file.py
libsndfile-1.0.21/src/interleave.c
libsndfile-1.0.21/src/sfconfig.h
libsndfile-1.0.21/src/Symbols.static
libsndfile-1.0.21/src/test_endswap.tpl
libsndfile-1.0.21/src/svx.c
libsndfile-1.0.21/src/windows.c
libsndfile-1.0.21/src/sndfile.h.in
libsndfile-1.0.21/src/wav.c
libsndfile-1.0.21/src/txw.c
libsndfile-1.0.21/src/make-static-lib-hidden-privates.sh
libsndfile-1.0.21/src/chanmap.c
libsndfile-1.0.21/src/wav_w64.h
libsndfile-1.0.21/src/w64.c
libsndfile-1.0.21/src/chanmap.h
libsndfile-1.0.21/src/binheader_writef_check.py
libsndfile-1.0.21/src/voc.c
libsndfile-1.0.21/src/dither.c
libsndfile-1.0.21/src/sndfile.hh
libsndfile-1.0.21/src/dwvw.c
libsndfile-1.0.21/src/raw.c
libsndfile-1.0.21/src/ulaw.c
libsndfile-1.0.21/src/pcm.c
libsndfile-1.0.21/src/test_log_printf.c
libsndfile-1.0.21/src/gsm610.c
libsndfile-1.0.21/src/double64.c
libsndfile-1.0.21/src/Makefile.in
libsndfile-1.0.21/src/audio_detect.c
libsndfile-1.0.21/src/sds.c
libsndfile-1.0.21/src/nist.c
libsndfile-1.0.21/src/wav_w64.c
libsndfile-1.0.21/src/avr.c
libsndfile-1.0.21/src/htk.c
libsndfile-1.0.21/src/sf_unistd.h
libsndfile-1.0.21/src/test_float.c
libsndfile-1.0.21/src/libsndfile-1.def
libsndfile-1.0.21/src/dwd.c
libsndfile-1.0.21/src/au.c
libsndfile-1.0.21/src/ogg.c
libsndfile-1.0.21/src/alaw.c
libsndfile-1.0.21/src/mpc2k.c
libsndfile-1.0.21/src/rx2.c
libsndfile-1.0.21/src/macbinary3.c
libsndfile-1.0.21/src/test_endswap.def
libsndfile-1.0.21/src/command.c
libsndfile-1.0.21/src/paf.c
libsndfile-1.0.21/src/rf64.c
libsndfile-1.0.21/src/float32.c
libsndfile-1.0.21/src/file_io.c
libsndfile-1.0.21/src/sd2.c
libsndfile-1.0.21/src/vox_adpcm.c
libsndfile-1.0.21/src/test_file_io.c
libsndfile-1.0.21/src/aiff.c
libsndfile-1.0.21/src/broadcast.c
libsndfile-1.0.21/src/chunk.c
libsndfile-1.0.21/src/test_endswap.c
libsndfile-1.0.21/src/wve.c
libsndfile-1.0.21/src/sndfile.c
libsndfile-1.0.21/src/sfendian.h
libsndfile-1.0.21/src/mat4.c
libsndfile-1.0.21/src/common.c
libsndfile-1.0.21/src/ms_adpcm.c
libsndfile-1.0.21/src/test_main.c
libsndfile-1.0.21/src/Symbols.os2
libsndfile-1.0.21/src/Symbols.darwin
libsndfile-1.0.21/src/G72x/
libsndfile-1.0.21/src/G72x/g721.c
libsndfile-1.0.21/src/G72x/README.original
libsndfile-1.0.21/src/G72x/g723_16.c
libsndfile-1.0.21/src/G72x/Makefile.in
libsndfile-1.0.21/src/G72x/g72x.h
libsndfile-1.0.21/src/G72x/ChangeLog
libsndfile-1.0.21/src/G72x/g72x_test.c
libsndfile-1.0.21/src/G72x/g723_24.c
libsndfile-1.0.21/src/G72x/Makefile.am
libsndfile-1.0.21/src/G72x/g723_40.c
libsndfile-1.0.21/src/G72x/g72x.c
libsndfile-1.0.21/src/G72x/README
libsndfile-1.0.21/src/G72x/g72x_priv.h
libsndfile-1.0.21/src/caf.c
libsndfile-1.0.21/src/GSM610/
libsndfile-1.0.21/src/GSM610/lpc.c
libsndfile-1.0.21/src/GSM610/long_term.c
libsndfile-1.0.21/src/GSM610/gsm_destroy.c
libsndfile-1.0.21/src/GSM610/gsm_decode.c
libsndfile-1.0.21/src/GSM610/gsm_create.c
libsndfile-1.0.21/src/GSM610/Makefile.in
libsndfile-1.0.21/src/GSM610/config.h
libsndfile-1.0.21/src/GSM610/add.c
libsndfile-1.0.21/src/GSM610/ChangeLog
libsndfile-1.0.21/src/GSM610/decode.c
libsndfile-1.0.21/src/GSM610/code.c
libsndfile-1.0.21/src/GSM610/table.c
libsndfile-1.0.21/src/GSM610/gsm.h
libsndfile-1.0.21/src/GSM610/COPYRIGHT
libsndfile-1.0.21/src/GSM610/gsm610_priv.h
libsndfile-1.0.21/src/GSM610/rpe.c
libsndfile-1.0.21/src/GSM610/short_term.c
libsndfile-1.0.21/src/GSM610/gsm_option.c
libsndfile-1.0.21/src/GSM610/gsm_encode.c
libsndfile-1.0.21/src/GSM610/Makefile.am
libsndfile-1.0.21/src/GSM610/preprocess.c
libsndfile-1.0.21/src/GSM610/README
libsndfile-1.0.21/src/Makefile.am
libsndfile-1.0.21/src/flac.c
libsndfile-1.0.21/src/test_main.h
libsndfile-1.0.21/src/g72x.c
libsndfile-1.0.21/src/xi.c
libsndfile-1.0.21/src/ima_oki_adpcm.c
libsndfile-1.0.21/configure.ac
libsndfile-1.0.21/shave-libtool.in
libsndfile-1.0.21/shave.in
libsndfile-1.0.21/regtest/
libsndfile-1.0.21/regtest/sndfile-regtest.c
libsndfile-1.0.21/regtest/Makefile.in
libsndfile-1.0.21/regtest/database.c
libsndfile-1.0.21/regtest/regtest.h
libsndfile-1.0.21/regtest/Makefile.am
libsndfile-1.0.21/regtest/checksum.c
libsndfile-1.0.21/tests/
libsndfile-1.0.21/tests/write_read_test.c
libsndfile-1.0.21/tests/generate.h
libsndfile-1.0.21/tests/stdio_test.c
libsndfile-1.0.21/tests/write_read_test.def
libsndfile-1.0.21/tests/checksum_test.c
libsndfile-1.0.21/tests/utils.def
libsndfile-1.0.21/tests/alaw_test.c
libsndfile-1.0.21/tests/pipe_test.c
libsndfile-1.0.21/tests/pcm_test.def
libsndfile-1.0.21/tests/scale_clip_test.c
libsndfile-1.0.21/tests/benchmark.tpl
libsndfile-1.0.21/tests/ogg_test.c
libsndfile-1.0.21/tests/command_test.c
libsndfile-1.0.21/tests/dither_test.c
libsndfile-1.0.21/tests/fix_this.c
libsndfile-1.0.21/tests/win32_ordinal_test.c
libsndfile-1.0.21/tests/benchmark.def
libsndfile-1.0.21/tests/error_test.c
libsndfile-1.0.21/tests/Makefile.in
libsndfile-1.0.21/tests/locale_test.c
libsndfile-1.0.21/tests/pipe_test.tpl
libsndfile-1.0.21/tests/multi_file_test.c
libsndfile-1.0.21/tests/write_read_test.tpl
libsndfile-1.0.21/tests/aiff_rw_test.c
libsndfile-1.0.21/tests/scale_clip_test.tpl
libsndfile-1.0.21/tests/scale_clip_test.def
libsndfile-1.0.21/tests/misc_test.c
libsndfile-1.0.21/tests/peak_chunk_test.c
libsndfile-1.0.21/tests/pcm_test.tpl
libsndfile-1.0.21/tests/lossy_comp_test.c
libsndfile-1.0.21/tests/generate.c
libsndfile-1.0.21/tests/ulaw_test.c
libsndfile-1.0.21/tests/floating_point_test.tpl
libsndfile-1.0.21/tests/benchmark.c
libsndfile-1.0.21/tests/utils.tpl
libsndfile-1.0.21/tests/string_test.c
libsndfile-1.0.21/tests/pipe_test.def
libsndfile-1.0.21/tests/utils.c
libsndfile-1.0.21/tests/raw_test.c
libsndfile-1.0.21/tests/header_test.tpl
libsndfile-1.0.21/tests/dft_cmp.c
libsndfile-1.0.21/tests/header_test.c
libsndfile-1.0.21/tests/external_libs_test.c
libsndfile-1.0.21/tests/virtual_io_test.c
libsndfile-1.0.21/tests/vorbis_test.c
libsndfile-1.0.21/tests/largefile_test.c
libsndfile-1.0.21/tests/cpp_test.cc
libsndfile-1.0.21/tests/header_test.def
libsndfile-1.0.21/tests/win32_test.c
libsndfile-1.0.21/tests/stdin_test.c
libsndfile-1.0.21/tests/pcm_test.c
libsndfile-1.0.21/tests/dwvw_test.c
libsndfile-1.0.21/tests/sfversion.c
libsndfile-1.0.21/tests/floating_point_test.def
libsndfile-1.0.21/tests/Makefile.am
libsndfile-1.0.21/tests/floating_point_test.c
libsndfile-1.0.21/tests/utils.h
libsndfile-1.0.21/tests/stdout_test.c
libsndfile-1.0.21/tests/dft_cmp.h
libsndfile-1.0.21/tests/headerless_test.c
libsndfile-1.0.21/tests/test_wrapper.sh.in
libsndfile-1.0.21/Cfg/
libsndfile-1.0.21/Cfg/config.sub
libsndfile-1.0.21/Cfg/compile
libsndfile-1.0.21/Cfg/config.guess
libsndfile-1.0.21/Cfg/ltmain.sh
libsndfile-1.0.21/Cfg/missing
libsndfile-1.0.21/Cfg/depcomp
libsndfile-1.0.21/Cfg/install-sh
libsndfile-1.0.21/COPYING
libsndfile-1.0.21/Makefile.am
libsndfile-1.0.21/aclocal.m4
libsndfile-1.0.21/README
libsndfile-1.0.21/libsndfile.spec.in

```

So I configured it, this is what I get:

```
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
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
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for autogen... no
checking for wine... yes
checking whether ln -s works... yes
checking for ANSI C header files... (cached) yes
checking endian.h usability... yes
checking endian.h presence... yes
checking for endian.h... yes
checking byteswap.h usability... yes
checking byteswap.h presence... yes
checking for byteswap.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking whether S_IRGRP is declared... yes
checking C99 struct flexible array support... yes
checking size of wchar_t... 4
checking size of short... 2
checking size of int... 4
checking size of long... 4
checking size of float... 4
checking size of double... 8
checking size of void*... 4
checking size of size_t... 4
checking size of int64_t... 8
checking size of long long... 8
checking size of off_t... 4
checking size of loff_t... 8
checking size of off64_t... 0
checking for getconf... getconf
checking for CFLAGS value to request large file support... -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
checking for LDFLAGS value to request large file support... 
checking for LIBS value to request large file support... 
checking for _FILE_OFFSET_BITS... 64
checking for _LARGEFILE_SOURCE... 1
checking for _LARGE_FILES... no
checking size of off_t... 8
checking for ssize_t... yes
checking size of ssize_t... 4
checking processor byte ordering... little
checking for malloc... yes
checking for calloc... yes
checking for realloc... yes
checking for free... yes
checking for open... yes
checking for read... yes
checking for write... yes
checking for lseek... yes
checking for pread... yes
checking for pwrite... yes
checking for fstat... yes
checking for ftruncate... yes
checking for fsync... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for gmtime... yes
checking for gmtime_r... yes
checking for localtime... yes
checking for localtime_r... yes
checking for gettimeofday... yes
checking for mmap... yes
checking for getpagesize... yes
checking for setlocale... yes
checking for floor in -lm... yes
checking for floor... yes
checking for ceil... yes
checking for fmod... yes
checking for lrint... yes
checking for lrintf... yes
checking for octave... no
checking for mkoctfile... no
checking for octave-config... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for flac >= 1.2.1 ... no
checking for ogg >= 1.1.3 ... no
checking for vorbis >= 1.2.3 ... no
checking for vorbisenc >= 1.2.3 ... no
configure: WARNING:

*** One or more of the external libraries (ie libflac, libogg and
*** libvorbis) is either missing (possibly only the development
*** headers) or is of an unsupported version.
***
*** Unfortunately, for ease of maintenance, the external libs
*** are an all or nothing affair.

checking for sqlite3 >= 3.2 ... no
checking processor clipping capabilities... negative
checking alsa/asoundlib.h usability... yes
checking alsa/asoundlib.h presence... yes
checking for alsa/asoundlib.h... yes
configure: WARNING: Touching files in directory tests/.
checking if gcc accepts -std=gnu99... yes
checking for version of gcc... 4.6
checking if gcc accepts -Wextra... yes
checking if g++ accepts -Wextra... yes
checking if gcc accepts -Wdeclaration-after-statement... yes
checking if gcc accepts -Wpointer-arith... yes
checking if gcc accepts -funsigned-char... yes
checking for sed... /bin/sed
configure: creating ./config.status
config.status: creating shave
config.status: creating shave-libtool
config.status: creating src/sndfile.h
config.status: creating src/Makefile
config.status: creating src/GSM610/Makefile
config.status: creating src/G72x/Makefile
config.status: creating man/Makefile
config.status: creating examples/Makefile
config.status: creating tests/Makefile
config.status: creating regtest/Makefile
config.status: creating M4/Makefile
config.status: creating doc/Makefile
config.status: creating Win32/Makefile
config.status: creating Octave/Makefile
config.status: creating programs/Makefile
config.status: creating doc/libsndfile.css
config.status: creating Makefile
config.status: creating libsndfile.spec
config.status: creating sndfile.pc
config.status: creating tests/test_wrapper.sh
config.status: creating build-test-tarball.mk
config.status: creating src/config.h
config.status: executing depfiles commands
config.status: executing libtool commands

-=-=-=-=-=-=-=-=-=-= Configuration Complete =-=-=-=-=-=-=-=-=-=-

  Configuration summary :

    libsndfile cersion : .................. 1.0.21

    Host CPU : ............................ i686
    Host Vendor : ......................... pc
    Host OS : ............................. linux-gnu

    Experimental code : ................... no
    Using ALSA in example programs : ...... yes
    External FLAC/Ogg/Vorbis : ............ no

  Tools :

    Compiler is GCC : ..................... yes
    GCC version : ......................... 4.6

  Installation directories :

    Library directory : ................... /usr/local/lib
    Program directory : ................... /usr/local/bin
    Pkgconfig directory : ................. /usr/local/lib/pkgconfig
    HTML docs directory : ................. /usr/local/share/doc/libsndfile1-dev/html

Compiling some other packages against libsndfile may require
the addition of "/usr/local/lib/pkgconfig" to the
PKG_CONFIG_PATH environment variable.

```

Then I tried to configure mednafen once more and i got the error "error: *** libsndfile >= 1.0.2 not found!" again.

Any help would be more than appreciated. Thank you! :D

---

### Post by pardalet on 2013-01-05
Configuring is not enough, you've got to compile and install:

```
make
sudo make install
```



And to avoid trouble when compiling the game, do what the libsndfile configurer suggests at the end:

> Compiling some other packages against libsndfile may require
> the addition of "/usr/local/lib/pkgconfig" to the
> PKG_CONFIG_PATH environment variable.


You can do it this way:

```
PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig
```

---

### Post by bobayoga on 2013-01-05
I must be doing something wrong.

Was I supposed to copy that code literaly? ```
PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig
```

Or was I supposed to replace PKG_CONFIG_PATH with somthing else? And besides, I tried to locate pkgconfig because it was not located in usr/local/lib:

```
$ locate pkgconfig
/usr/lib/pkgconfig
/usr/lib/pkgconfig/banshee-collection-indexer.pc
/usr/lib/pkgconfig/banshee-core.pc
/usr/lib/pkgconfig/banshee-hyena-data-sqlite.pc
/usr/lib/pkgconfig/banshee-hyena-gui.pc
/usr/lib/pkgconfig/banshee-hyena.pc
/usr/lib/pkgconfig/banshee-lastfm-gui.pc
/usr/lib/pkgconfig/banshee-lastfm.pc
/usr/lib/pkgconfig/banshee-mono-media.pc
/usr/lib/pkgconfig/banshee-musicbrainz.pc
/usr/lib/pkgconfig/banshee-nowplaying.pc
/usr/lib/pkgconfig/banshee-services.pc
/usr/lib/pkgconfig/banshee-thickclient.pc
/usr/lib/pkgconfig/banshee-webbrowser.pc
/usr/lib/pkgconfig/dbus-python.pc
/usr/lib/pkgconfig/fontutil.pc
/usr/lib/pkgconfig/ginn.pc
/usr/lib/pkgconfig/ibus-table.pc
/usr/lib/pkgconfig/libgdiplus.pc
/usr/lib/pkgconfig/libquvi-scripts.pc
/usr/lib/pkgconfig/nautilus-sendto.pc
/usr/lib/pkgconfig/notify-python.pc
/usr/lib/pkgconfig/pm-utils.pc
/usr/lib/pkgconfig/pygtksourceview-2.0.pc
/usr/lib/pkgconfig/python2.pc
/usr/lib/pkgconfig/xorg-wacom.pc
/usr/lib/rpm/pkgconfigdeps.sh
/usr/lib/rpm/fileattrs/pkgconfig.attr
/usr/share/pkgconfig
/usr/share/gtksourceview-2.0/language-specs/pkgconfig.lang
/usr/share/gtksourceview-3.0/language-specs/pkgconfig.lang
/usr/share/pkgconfig/gnome-icon-theme.pc
/usr/share/pkgconfig/iso-codes.pc
/usr/share/pkgconfig/mobile-broadband-provider-info.pc
/usr/share/pkgconfig/shared-desktop-ontologies.pc
/usr/share/pkgconfig/shared-mime-info.pc
/usr/share/pkgconfig/udev.pc
/usr/share/pkgconfig/udisks.pc
/usr/share/pkgconfig/usbutils.pc
/usr/share/pkgconfig/xbitmaps.pc
/usr/share/pkgconfig/xkeyboard-config.pc
/usr/share/pkgconfig/yelp-xsl.pc

```

So I'm a little confused. I don't really know what pkgconfig is, but not only is it not located in /usr/local/lib, it's actually located in multiple locations. I assume it's a directory, correct?

So to summarize:

I cannot type "make", or "make install" yet, since I always get the error message about libsndfile when I enter "./configure"

I tried the code you gave me using all locations of pkgconfig

```
PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig
```

```
PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/share/pkgconfig
```

```
PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/lib/pkgconfig
```

When I do this, I don't get a message of any kind, it's just as if I entered nothing and pressed the enter key.

So after all that I try ./configure again, and I still get this:

```
checking for LIBCDIO... yes
checking for SNDFILE... no
configure: error: *** libsndfile >= 1.0.2 not found!

```

---

### Post by pardalet on 2013-01-05
I meant you should make && make install the libsndfile source code (after configuring it) before you could properly configure the game.


Regarding the environment variable it certainly seems that pkgconfig is located at /usr/lib/ instead of /usr/local/lib. Besides, this variable doesn't seem to exist, at least on my system.
So, what you should do first of all (on a new terminal) is check whether the variable exists:

```
echo $PKG_CONFIG_PATH
```

If it returns nothing, then you should execute:

```
PKG_CONFIG_PATH=/usr/local/lib/pkgconfig
```

If it does return something, which is different from /usr/lib/pkgconfig, then you should do:

```
PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig
```


Be aware that when you close the terminal the variable is lost. So you need to do this after you compile & install libsndfile and before configuring (and compiling and installing) the game, all the time on the same terminal.

---

### Post by bobayoga on 2013-01-05
Yes HAHAHA!

Everything worked!

Please accept my sincere gratitude.

May you be well, friend! 

:D

P.S. to anyone reading this who had the same problem, if you ever get "permission denied", it can be because you did your stuff on an external hard drive or a USB key.

---

