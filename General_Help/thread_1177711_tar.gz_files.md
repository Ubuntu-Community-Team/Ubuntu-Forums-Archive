---
title: "tar.gz files"
date: 2009-06-03
forum: General Help
---

### Post by UncleMonty on 2009-06-03
What do I do with these files? I'm fed up with downloading files like this as I have no idea what to do with them. :(

---

### Post by SuperSonic4 on 2009-06-03
They can be anything. Tarballs are just compressed files which can be music, video, source code or any/all of the above.

If it's source code then extract the tarball and look for a README file which should tell you what to do.

*Usually* it will be something like ```
cd /path/to/dir
./configure
make
sudo make install
```

But really, check the readme, or better yet check the repos or getdeb.net for the program in question. Out of curiosity, which program are you after?

---

### Post by michy99 on 2009-06-03
Is the program you want in the repositories? It would be much easier to install. Go to System->Administration->Synaptic Package Manager and search for what you want.

---

### Post by mdawg414 on 2009-06-03
You don't know how to extract them? Is that the question?

Try this:

```

tar -xzf mytar.tar.gz

```

---

### Post by UncleMonty on 2009-06-03
> **SuperSonic4 said:**
> They can be anything. Tarballs are just compressed files which can be music, video, source code or any/all of the above.

If it's source code then extract the tarball and look for a README file which should tell you what to do.

*Usually* it will be something like ```
cd /path/to/dir
./configure
make
sudo make install
```

But really, check the readme, or better yet check the repos or getdeb.net for the program in question. Out of curiosity, which program are you after?

Vice 2.1

---

### Post by UncleMonty on 2009-06-03
> **mdawg414 said:**
> You don't know how to extract them? Is that the question?

Try this:

```

tar -xzf mytar.tar.gz

```

I know how to extract them, just no idea where to go from there!

---

### Post by michy99 on 2009-06-03
Vice is in the repositories, but not the latest version. If you want to compile the version you have downloaded, open a terminal, go to the directory you have extracted and enter these commands:```
./configure
make
sudo make install
```
If get errors, you will probably need to install some other files before it will compile.

---

### Post by UncleMonty on 2009-06-03
> **michy99 said:**
> Vice is in the repositories, but not the latest version. If you want to compile the version you have downloaded, open a terminal, go to the directory you have extracted and enter these commands:```
./configure
make
sudo make install
```
If get errors, you will probably need to install some other files before it will compile.

"go to the directory you have extracted"

How do I do that? (Sorry I'm not as computer savvy as most linux users).

---

### Post by logos34 on 2009-06-03
yes, exactly what application is this?  maybe there's a deb out there if not in the repos

---

### Post by michy99 on 2009-06-03
If you extracted the tar.gz file, where was it? On your Desktop?

---

### Post by UncleMonty on 2009-06-03
> **michy99 said:**
> If you extracted the tar.gz file, where was it? On your Desktop?

Yes it's on my desktop.

---

### Post by michy99 on 2009-06-03
In a terminal enter```
cd Desktop
```
Note that the D is capitol. Linux is case sensitive. Now enter```
ls
``` and post the output.

---

### Post by UncleMonty on 2009-06-03
> **michy99 said:**
> In a terminal enter```
cd Desktop
```
Note that the D is capitol. Linux is case sensitive. Now enter```
ls
``` and post the output.

steve@Iago:~$ cd Desktop
steve@Iago:~/Desktop$ ls
vice-2.1

---

### Post by UncleMonty on 2009-06-03
> **michy99 said:**
> Vice is in the repositories, but not the latest version. If you want to compile the version you have downloaded, open a terminal, go to the directory you have extracted and enter these commands:```
./configure
make
sudo make install
```
If get errors, you will probably need to install some other files before it will compile.

"go to the directory you have extracted"

How do I do that? (Sorry I'm not as computer savvy as most linux users).

---

### Post by michy99 on 2009-06-03
Okay, now ```
cd vice-2.1
```
This puts you in the extracted directory. Now enter```
./configure
``` and post the results.

---

### Post by UncleMonty on 2009-06-03
> **michy99 said:**
> Okay, now ```
cd vice-2.1
```
This puts you in the extracted directory. Now enter```
./configure
``` and post the results.

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
no explicit checking for XFree86 fullscreen requested, disabling fullscreen...
using TextField widget.
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
checking dependency style of gcc... gcc3
using x86-specific optimizing options
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
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
checking linux/hardsid.h usability... no
checking linux/hardsid.h presence... no
checking for linux/hardsid.h... no
checking how to run the C preprocessor... gcc -E
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for bison... no
checking for byacc... no
checking for flex... no
checking for lex... no
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for gettext in libc... yes
checking for gettext in libintl... no
checking for msgfmt... no
found xgettext program is not GNU xgettext; ignore it
configure: WARNING: msgfmt not found, falling back to default catalogs (x86/Linux)
checking for perl... /usr/bin/perl
checking if the compiler accepts --param inline-unit-growth=60... yes
checking if the compiler accepts --param max-inline-insns-single=600... yes
checking for c++... c++
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for sys/types.h... (cached) yes
checking for off_t... yes
checking for pid_t... yes
checking for size_t... yes
checking for inline... inline
checking whether byte ordering is bigendian... no
checking for unsigned short... yes
checking size of unsigned short... 2
checking for unsigned int... yes
checking size of unsigned int... 4
checking for unsigned long... yes
checking size of unsigned long... 4
checking whether gcc needs -traditional... no
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking direct.h usability... no
checking direct.h presence... no
checking for direct.h... no
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
checking for unistd.h... (cached) yes
checking for strings.h... (cached) yes
checking sys/dirent.h usability... no
checking sys/dirent.h presence... no
checking for sys/dirent.h... no
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for sys/stat.h... (cached) yes
checking for inttypes.h... (cached) yes
checking libgen.h usability... yes
checking libgen.h presence... yes
checking for libgen.h... yes
checking dir.h usability... no
checking dir.h presence... no
checking for dir.h... no
checking io.h usability... no
checking io.h presence... no
checking for io.h... no
checking process.h usability... no
checking process.h presence... no
checking for process.h... no
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking commctrl.h usability... no
checking commctrl.h presence... no
checking for commctrl.h... no
checking shlobj.h usability... no
checking shlobj.h presence... no
checking for shlobj.h... no
checking winioctl.h usability... no
checking winioctl.h presence... no
checking for winioctl.h... no
checking for regexp.h... yes
checking whether sys_siglist is declared... yes
checking linux/joystick.h usability... yes
checking linux/joystick.h presence... yes
checking for linux/joystick.h... yes
checking whether linux/joystick.h supports digital joysticks... no
checking machine/joystick.h usability... no
checking machine/joystick.h presence... no
checking for machine/joystick.h... no
checking sys/joystick.h usability... no
checking sys/joystick.h presence... no
checking for sys/joystick.h... no
checking for hid_get_report_desc in -lusbhid... no
checking for hid_get_report_desc in -lusb... no
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
checking for sqrt in -lm... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for zlibVersion in -lz... (cached) yes
checking for sys/types.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking for gethostbyname in -lnsl... yes
checking for gethostbyname in -lsocket... no
checking for gethostbyname in -lbsd... no
checking for gethostbyname in -lnet... no
checking for gethostbyname in -linet... no
checking for gethostbyname in -lwatt... no
checking for socket... yes
checking for send... yes
checking for bind... yes
checking for listen... yes
checking for gethostbyname... yes
checking for connect... yes
checking for recv... yes
checking for accept... yes
checking for htons... yes
checking for htonl... yes
checking for getdtablesize... yes
checking for getrlimit... yes
checking if IPV6 should be enabled... yes
checking struct sockaddr::ss_family... yes
checking for gethostbyname2... yes
checking cwsid.h usability... no
checking cwsid.h presence... no
checking for cwsid.h... no
checking alsa/asoundlib.h usability... no
checking alsa/asoundlib.h presence... no
checking for alsa/asoundlib.h... no
checking linux/soundcard.h usability... yes
checking linux/soundcard.h presence... yes
checking for linux/soundcard.h... yes
checking machine/soundcard.h usability... no
checking machine/soundcard.h presence... no
checking for machine/soundcard.h... no
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking soundcard.h usability... no
checking soundcard.h presence... no
checking for soundcard.h... no
checking for _oss_ioctl in -lossaudio... no
checking dmedia/audio.h usability... no
checking dmedia/audio.h presence... no
checking for dmedia/audio.h... no
checking sys/audioio.h usability... no
checking sys/audioio.h presence... no
checking for sys/audioio.h... no
checking esd.h usability... no
checking esd.h presence... no
checking for esd.h... no
checking UMS/UMSAudioDevice.h usability... no
checking UMS/UMSAudioDevice.h presence... no
checking for UMS/UMSAudioDevice.h... no
checking lame/lame.h usability... no
checking lame/lame.h presence... no
checking for lame/lame.h... no
checking for fc-cache... /usr/bin/fc-cache
checking for working memcmp... yes
checking return type of signal handlers... void
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for u_short... yes
checking for gettimeofday in -lbsd... no
checking for gettimeofday... yes
checking for memmove... yes
checking for atexit... yes
checking for strerror... yes
checking for strcasecmp... yes
checking for strncasecmp... yes
checking for telldir... yes
checking for seekdir... yes
checking for rewinddir... yes
checking for dirname... yes
checking for mkstemp... yes
checking for swab... yes
checking for getcwd... yes
checking for readline in -lreadline... no
checking for readline in -lreadline... no
checking for readline in -lreadline... no
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for png_check_sig in -lpng... yes
checking gif_lib.h usability... no
checking gif_lib.h presence... no
checking for gif_lib.h... no
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking for jpeg_CreateCompress in -ljpeg... yes
checking for X... no
checking for gethostbyname in -lnsl... (cached) yes
checking for gethostbyname in -lsocket... (cached) no
checking for gethostbyname in -lbsd... (cached) no
checking for IceConnectionNumber in -lICE... no
checking for SmFreeProperty in -lSM... no
checking for XCreateWindow in -lX11... no
checking for XQueryExtension in -lXext... no
checking for X11/extensions/Xvlib.h... no
checking for XvQueryExtension in -lXv... no
checking for XtToolkitInitialize in -lXt... no
checking for XInternAtom in -lXmu... no
checking for XpmCreatePixmapFromData in -lXpm... no
checking for XawFormDoLayout in -lXaw... no
checking for X11/extensions/XShm.h... no

+++ Warning: the following important X11 libraries were not found:  X11 Xt Xmu Xaw
+++ You might have to edit the Makefile by hand to compile properly

checking X11/Sunkeysym.h usability... no
checking X11/Sunkeysym.h presence... no
checking for X11/Sunkeysym.h... no
checking X11/xpm.h usability... no
checking X11/xpm.h presence... no
checking for X11/xpm.h... no
checking xpm.h usability... no
checking xpm.h presence... no
checking for xpm.h... no
checking for GL/glx.h... no
checking opencbm.h usability... no
checking opencbm.h presence... no
checking for opencbm.h... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating build/Makefile
config.status: creating data/Makefile
config.status: creating data/C128/Makefile
config.status: creating data/C64/Makefile
config.status: creating data/C64DTV/Makefile
config.status: creating data/CBM-II/Makefile
config.status: creating data/DRIVES/Makefile
config.status: creating data/PET/Makefile
config.status: creating data/PLUS4/Makefile
config.status: creating data/PRINTER/Makefile
config.status: creating data/VIC20/Makefile
config.status: creating data/fonts/Makefile
config.status: creating doc/Makefile
config.status: creating doc/html/Makefile
config.status: creating man/Makefile
config.status: creating src/Makefile
config.status: creating src/arch/Makefile
config.status: creating src/arch/amigaos/Makefile
config.status: creating src/arch/beos/Makefile
config.status: creating src/arch/msdos/Makefile
config.status: creating src/arch/os2/Makefile
config.status: creating src/arch/os2/dialogs/Makefile
config.status: creating src/arch/os2/kbd/Makefile
config.status: creating src/arch/os2/snippets/Makefile
config.status: creating src/arch/os2/vac++/Makefile
config.status: creating src/arch/riscos/Makefile
config.status: creating src/arch/unix/Makefile
config.status: creating src/arch/unix/gp2x/Makefile
config.status: creating src/arch/unix/gui/Makefile
config.status: creating src/arch/unix/readline/Makefile
config.status: creating src/arch/unix/x11/Makefile
config.status: creating src/arch/unix/x11/gnome/Makefile
config.status: creating src/arch/unix/x11/xaw/Makefile
config.status: creating src/arch/unix/x11/xaw/widgets/Makefile
config.status: creating src/arch/unix/macosx/Makefile
config.status: creating src/arch/unix/macosx/cocoa/Makefile
config.status: creating src/arch/unix/macosx/cocoa/view/Makefile
config.status: creating src/arch/unix/macosx/cocoa/menu/Makefile
config.status: creating src/arch/unix/macosx/cocoa/dialog/Makefile
config.status: creating src/arch/unix/macosx/Resources/Makefile
config.status: creating src/arch/unix/macosx/Resources/English.lproj/Makefile
config.status: creating src/arch/win32/Makefile
config.status: creating src/arch/win32/utils/Makefile
config.status: creating src/c128/Makefile
config.status: creating src/c64/Makefile
config.status: creating src/c64/cart/Makefile
config.status: creating src/c64dtv/Makefile
config.status: creating src/cbm2/Makefile
config.status: creating src/core/Makefile
config.status: creating src/crtc/Makefile
config.status: creating src/diskimage/Makefile
config.status: creating src/drive/Makefile
config.status: creating src/drive/iec/Makefile
config.status: creating src/drive/iec/c64exp/Makefile
config.status: creating src/drive/iec/plus4exp/Makefile
config.status: creating src/drive/iec128dcr/Makefile
config.status: creating src/drive/iecieee/Makefile
config.status: creating src/drive/ieee/Makefile
config.status: creating src/drive/tcbm/Makefile
config.status: creating src/fileio/Makefile
config.status: creating src/fsdevice/Makefile
config.status: creating src/gfxoutputdrv/Makefile
config.status: creating src/iecbus/Makefile
config.status: creating src/imagecontents/Makefile
config.status: creating src/lib/Makefile
config.status: creating src/lib/lpng/Makefile
config.status: creating src/lib/zlib/Makefile
config.status: creating src/monitor/Makefile
config.status: creating src/parallel/Makefile
config.status: creating src/pet/Makefile
config.status: creating src/plus4/Makefile
config.status: creating src/printerdrv/Makefile
config.status: creating src/raster/Makefile
config.status: creating src/rs232drv/Makefile
config.status: creating src/serial/Makefile
config.status: creating src/sid/Makefile
config.status: creating src/sounddrv/Makefile
config.status: creating src/tape/Makefile
config.status: creating src/vdc/Makefile
config.status: creating src/vdrive/Makefile
config.status: creating src/vic20/Makefile
config.status: creating src/vicii/Makefile
config.status: creating src/video/Makefile
config.status: creating src/version.h
config.status: creating po/Makefile.in
config.status: creating src/config.h
config.status: executing depfiles commands
config.status: executing default-1 commands
=== configuring in src/resid (/home/steve/Desktop/vice-2.1/src/resid)
configure: running /bin/bash ./configure '--prefix=/usr/local'  --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking whether the C++ compiler (g++ -g -Wall -O2 -funroll-loops -fomit-frame-pointer -fno-exceptions ) works... yes
checking for ar... ar
checking for ranlib... ranlib
checking for perl... /usr/bin/perl
checking how to run the C++ preprocessor... g++ -E
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
checking for int... yes
checking size of int... 4
checking for working bool... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating siddefs.h
config.status: executing depfiles commands
=== configuring in src/resid-fp (/home/steve/Desktop/vice-2.1/src/resid-fp)
configure: running /bin/bash ./configure '--prefix=/usr/local'  --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking whether the C++ compiler (g++ -g -Wall -O2 -msse ) works... yes
checking whether the C++ compiler (g++ -g -Wall -O2 -msse -fno-exceptions ) works... yes
checking whether the C++ compiler (g++ -g -Wall -O2 -msse -fno-exceptions -fno-exceptions -fno-pic ) works... yes
checking if the xmmintrin.h include can be used... yes
checking for ar... ar
checking for ranlib... ranlib
checking for perl... /usr/bin/perl
checking how to run the C++ preprocessor... g++ -E
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
checking for int... yes
checking size of int... 4
checking for working bool... yes
checking for logf... yes
checking for expf... yes
checking if the logf prototype is present... yes
checking if the expf prototype is present... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating siddefs-fp.h
config.status: executing depfiles commands
steve@Iago:~/Desktop/vice-2.1$

---

### Post by michy99 on 2009-06-03
Ok now enter```
make
``` and see what happens.

---

### Post by UncleMonty on 2009-06-03
> **michy99 said:**
> Ok now enter```
make
``` and see what happens.

It hasn't kept all the info for some reason. This is all that's left: 


ps/vdrive-rel.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT vdrive-snapshot.o -MD -MP -MF ".deps/vdrive-snapshot.Tpo" -c -o vdrive-snapshot.o vdrive-snapshot.c; \
	then mv -f ".deps/vdrive-snapshot.Tpo" ".deps/vdrive-snapshot.Po"; else rm -f ".deps/vdrive-snapshot.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT vdrive.o -MD -MP -MF ".deps/vdrive.Tpo" -c -o vdrive.o vdrive.c; \
	then mv -f ".deps/vdrive.Tpo" ".deps/vdrive.Po"; else rm -f ".deps/vdrive.Tpo"; exit 1; fi
rm -f libvdrive.a
ar cru libvdrive.a vdrive-bam.o vdrive-command.o vdrive-dir.o vdrive-iec.o vdrive-internal.o vdrive-rel.o vdrive-snapshot.o vdrive.o 
ranlib libvdrive.a
make[3]: Leaving directory `/home/steve/Desktop/vice-2.1/src/vdrive'
Making all in fsdevice
make[3]: Entering directory `/home/steve/Desktop/vice-2.1/src/fsdevice'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/vdrive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT fsdevice-close.o -MD -MP -MF ".deps/fsdevice-close.Tpo" -c -o fsdevice-close.o fsdevice-close.c; \
	then mv -f ".deps/fsdevice-close.Tpo" ".deps/fsdevice-close.Po"; else rm -f ".deps/fsdevice-close.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/vdrive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT fsdevice-cmdline-options.o -MD -MP -MF ".deps/fsdevice-cmdline-options.Tpo" -c -o fsdevice-cmdline-options.o fsdevice-cmdline-options.c; \
	then mv -f ".deps/fsdevice-cmdline-options.Tpo" ".deps/fsdevice-cmdline-options.Po"; else rm -f ".deps/fsdevice-cmdline-options.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/vdrive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT fsdevice-flush.o -MD -MP -MF ".deps/fsdevice-flush.Tpo" -c -o fsdevice-flush.o fsdevice-flush.c; \
	then mv -f ".deps/fsdevice-flush.Tpo" ".deps/fsdevice-flush.Po"; else rm -f ".deps/fsdevice-flush.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/vdrive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT fsdevice-open.o -MD -MP -MF ".deps/fsdevice-open.Tpo" -c -o fsdevice-open.o fsdevice-open.c; \
	then mv -f ".deps/fsdevice-open.Tpo" ".deps/fsdevice-open.Po"; else rm -f ".deps/fsdevice-open.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/vdrive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT fsdevice-read.o -MD -MP -MF ".deps/fsdevice-read.Tpo" -c -o fsdevice-read.o fsdevice-read.c; \
	then mv -f ".deps/fsdevice-read.Tpo" ".deps/fsdevice-read.Po"; else rm -f ".deps/fsdevice-read.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/vdrive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT fsdevice-resources.o -MD -MP -MF ".deps/fsdevice-resources.Tpo" -c -o fsdevice-resources.o fsdevice-resources.c; \
	then mv -f ".deps/fsdevice-resources.Tpo" ".deps/fsdevice-resources.Po"; else rm -f ".deps/fsdevice-resources.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/vdrive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT fsdevice-write.o -MD -MP -MF ".deps/fsdevice-write.Tpo" -c -o fsdevice-write.o fsdevice-write.c; \
	then mv -f ".deps/fsdevice-write.Tpo" ".deps/fsdevice-write.Po"; else rm -f ".deps/fsdevice-write.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/vdrive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT fsdevice.o -MD -MP -MF ".deps/fsdevice.Tpo" -c -o fsdevice.o fsdevice.c; \
	then mv -f ".deps/fsdevice.Tpo" ".deps/fsdevice.Po"; else rm -f ".deps/fsdevice.Tpo"; exit 1; fi
rm -f libfsdevice.a
ar cru libfsdevice.a fsdevice-close.o fsdevice-cmdline-options.o fsdevice-flush.o fsdevice-open.o fsdevice-read.o fsdevice-resources.o fsdevice-write.o fsdevice.o 
ranlib libfsdevice.a
make[3]: Leaving directory `/home/steve/Desktop/vice-2.1/src/fsdevice'
Making all in diskimage
make[3]: Entering directory `/home/steve/Desktop/vice-2.1/src/diskimage'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT diskimage.o -MD -MP -MF ".deps/diskimage.Tpo" -c -o diskimage.o diskimage.c; \
	then mv -f ".deps/diskimage.Tpo" ".deps/diskimage.Po"; else rm -f ".deps/diskimage.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT fsimage-check.o -MD -MP -MF ".deps/fsimage-check.Tpo" -c -o fsimage-check.o fsimage-check.c; \
	then mv -f ".deps/fsimage-check.Tpo" ".deps/fsimage-check.Po"; else rm -f ".deps/fsimage-check.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT fsimage-create.o -MD -MP -MF ".deps/fsimage-create.Tpo" -c -o fsimage-create.o fsimage-create.c; \
	then mv -f ".deps/fsimage-create.Tpo" ".deps/fsimage-create.Po"; else rm -f ".deps/fsimage-create.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT fsimage-gcr.o -MD -MP -MF ".deps/fsimage-gcr.Tpo" -c -o fsimage-gcr.o fsimage-gcr.c; \
	then mv -f ".deps/fsimage-gcr.Tpo" ".deps/fsimage-gcr.Po"; else rm -f ".deps/fsimage-gcr.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT fsimage-probe.o -MD -MP -MF ".deps/fsimage-probe.Tpo" -c -o fsimage-probe.o fsimage-probe.c; \
	then mv -f ".deps/fsimage-probe.Tpo" ".deps/fsimage-probe.Po"; else rm -f ".deps/fsimage-probe.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT fsimage.o -MD -MP -MF ".deps/fsimage.Tpo" -c -o fsimage.o fsimage.c; \
	then mv -f ".deps/fsimage.Tpo" ".deps/fsimage.Po"; else rm -f ".deps/fsimage.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT rawimage.o -MD -MP -MF ".deps/rawimage.Tpo" -c -o rawimage.o rawimage.c; \
	then mv -f ".deps/rawimage.Tpo" ".deps/rawimage.Po"; else rm -f ".deps/rawimage.Tpo"; exit 1; fi
rm -f libdiskimage.a
ar cru libdiskimage.a diskimage.o fsimage-check.o fsimage-create.o fsimage-gcr.o fsimage-probe.o fsimage.o rawimage.o
ranlib libdiskimage.a
make[3]: Leaving directory `/home/steve/Desktop/vice-2.1/src/diskimage'
Making all in iecbus
make[3]: Entering directory `/home/steve/Desktop/vice-2.1/src/iecbus'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/drive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT iecbus.o -MD -MP -MF ".deps/iecbus.Tpo" -c -o iecbus.o iecbus.c; \
	then mv -f ".deps/iecbus.Tpo" ".deps/iecbus.Po"; else rm -f ".deps/iecbus.Tpo"; exit 1; fi
rm -f libiecbus.a
ar cru libiecbus.a iecbus.o 
ranlib libiecbus.a
make[3]: Leaving directory `/home/steve/Desktop/vice-2.1/src/iecbus'
Making all in serial
make[3]: Entering directory `/home/steve/Desktop/vice-2.1/src/serial'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/drive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT fsdrive.o -MD -MP -MF ".deps/fsdrive.Tpo" -c -o fsdrive.o fsdrive.c; \
	then mv -f ".deps/fsdrive.Tpo" ".deps/fsdrive.Po"; else rm -f ".deps/fsdrive.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/drive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT serial-device.o -MD -MP -MF ".deps/serial-device.Tpo" -c -o serial-device.o serial-device.c; \
	then mv -f ".deps/serial-device.Tpo" ".deps/serial-device.Po"; else rm -f ".deps/serial-device.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/drive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT serial-iec-bus.o -MD -MP -MF ".deps/serial-iec-bus.Tpo" -c -o serial-iec-bus.o serial-iec-bus.c; \
	then mv -f ".deps/serial-iec-bus.Tpo" ".deps/serial-iec-bus.Po"; else rm -f ".deps/serial-iec-bus.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/drive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT serial-iec-device.o -MD -MP -MF ".deps/serial-iec-device.Tpo" -c -o serial-iec-device.o serial-iec-device.c; \
	then mv -f ".deps/serial-iec-device.Tpo" ".deps/serial-iec-device.Po"; else rm -f ".deps/serial-iec-device.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/drive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT serial-iec-lib.o -MD -MP -MF ".deps/serial-iec-lib.Tpo" -c -o serial-iec-lib.o serial-iec-lib.c; \
	then mv -f ".deps/serial-iec-lib.Tpo" ".deps/serial-iec-lib.Po"; else rm -f ".deps/serial-iec-lib.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/drive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT serial-iec.o -MD -MP -MF ".deps/serial-iec.Tpo" -c -o serial-iec.o serial-iec.c; \
	then mv -f ".deps/serial-iec.Tpo" ".deps/serial-iec.Po"; else rm -f ".deps/serial-iec.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/drive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT serial-realdevice.o -MD -MP -MF ".deps/serial-realdevice.Tpo" -c -o serial-realdevice.o serial-realdevice.c; \
	then mv -f ".deps/serial-realdevice.Tpo" ".deps/serial-realdevice.Po"; else rm -f ".deps/serial-realdevice.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/drive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT serial-trap.o -MD -MP -MF ".deps/serial-trap.Tpo" -c -o serial-trap.o serial-trap.c; \
	then mv -f ".deps/serial-trap.Tpo" ".deps/serial-trap.Po"; else rm -f ".deps/serial-trap.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/drive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT serial.o -MD -MP -MF ".deps/serial.Tpo" -c -o serial.o serial.c; \
	then mv -f ".deps/serial.Tpo" ".deps/serial.Po"; else rm -f ".deps/serial.Tpo"; exit 1; fi
rm -f libserial.a
ar cru libserial.a fsdrive.o serial-device.o serial-iec-bus.o serial-iec-device.o serial-iec-lib.o serial-iec.o serial-realdevice.o serial-trap.o serial.o 
ranlib libserial.a
make[3]: Leaving directory `/home/steve/Desktop/vice-2.1/src/serial'
Making all in parallel
make[3]: Entering directory `/home/steve/Desktop/vice-2.1/src/parallel'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/drive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT parallel-trap.o -MD -MP -MF ".deps/parallel-trap.Tpo" -c -o parallel-trap.o parallel-trap.c; \
	then mv -f ".deps/parallel-trap.Tpo" ".deps/parallel-trap.Po"; else rm -f ".deps/parallel-trap.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/drive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT parallel.o -MD -MP -MF ".deps/parallel.Tpo" -c -o parallel.o parallel.c; \
	then mv -f ".deps/parallel.Tpo" ".deps/parallel.Po"; else rm -f ".deps/parallel.Tpo"; exit 1; fi
rm -f libparallel.a
ar cru libparallel.a parallel-trap.o parallel.o 
ranlib libparallel.a
make[3]: Leaving directory `/home/steve/Desktop/vice-2.1/src/parallel'
Making all in tape
make[3]: Entering directory `/home/steve/Desktop/vice-2.1/src/tape'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT t64.o -MD -MP -MF ".deps/t64.Tpo" -c -o t64.o t64.c; \
	then mv -f ".deps/t64.Tpo" ".deps/t64.Po"; else rm -f ".deps/t64.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT tap.o -MD -MP -MF ".deps/tap.Tpo" -c -o tap.o tap.c; \
	then mv -f ".deps/tap.Tpo" ".deps/tap.Po"; else rm -f ".deps/tap.Tpo"; exit 1; fi
tap.c: In function ‘tap_cbm_read_byte’:
tap.c:225: warning: inlining failed in call to ‘tap_get_pulse’: call is unlikely and code size would grow
tap.c:299: warning: called from here
tap.c:225: warning: inlining failed in call to ‘tap_get_pulse’: call is unlikely and code size would grow
tap.c:299: warning: called from here
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT tape-internal.o -MD -MP -MF ".deps/tape-internal.Tpo" -c -o tape-internal.o tape-internal.c; \
	then mv -f ".deps/tape-internal.Tpo" ".deps/tape-internal.Po"; else rm -f ".deps/tape-internal.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT tape-snapshot.o -MD -MP -MF ".deps/tape-snapshot.Tpo" -c -o tape-snapshot.o tape-snapshot.c; \
	then mv -f ".deps/tape-snapshot.Tpo" ".deps/tape-snapshot.Po"; else rm -f ".deps/tape-snapshot.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT tape.o -MD -MP -MF ".deps/tape.Tpo" -c -o tape.o tape.c; \
	then mv -f ".deps/tape.Tpo" ".deps/tape.Po"; else rm -f ".deps/tape.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT tapeimage.o -MD -MP -MF ".deps/tapeimage.Tpo" -c -o tapeimage.o tapeimage.c; \
	then mv -f ".deps/tapeimage.Tpo" ".deps/tapeimage.Po"; else rm -f ".deps/tapeimage.Tpo"; exit 1; fi
rm -f libtape.a
ar cru libtape.a t64.o tap.o tape-internal.o tape-snapshot.o tape.o tapeimage.o 
ranlib libtape.a
make[3]: Leaving directory `/home/steve/Desktop/vice-2.1/src/tape'
Making all in imagecontents
make[3]: Entering directory `/home/steve/Desktop/vice-2.1/src/imagecontents'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/vdrive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT diskcontents-block.o -MD -MP -MF ".deps/diskcontents-block.Tpo" -c -o diskcontents-block.o diskcontents-block.c; \
	then mv -f ".deps/diskcontents-block.Tpo" ".deps/diskcontents-block.Po"; else rm -f ".deps/diskcontents-block.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/vdrive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT diskcontents-iec.o -MD -MP -MF ".deps/diskcontents-iec.Tpo" -c -o diskcontents-iec.o diskcontents-iec.c; \
	then mv -f ".deps/diskcontents-iec.Tpo" ".deps/diskcontents-iec.Po"; else rm -f ".deps/diskcontents-iec.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/vdrive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT diskcontents.o -MD -MP -MF ".deps/diskcontents.Tpo" -c -o diskcontents.o diskcontents.c; \
	then mv -f ".deps/diskcontents.Tpo" ".deps/diskcontents.Po"; else rm -f ".deps/diskcontents.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/vdrive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT imagecontents.o -MD -MP -MF ".deps/imagecontents.Tpo" -c -o imagecontents.o imagecontents.c; \
	then mv -f ".deps/imagecontents.Tpo" ".deps/imagecontents.Po"; else rm -f ".deps/imagecontents.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/vdrive    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT tapecontents.o -MD -MP -MF ".deps/tapecontents.Tpo" -c -o tapecontents.o tapecontents.c; \
	then mv -f ".deps/tapecontents.Tpo" ".deps/tapecontents.Po"; else rm -f ".deps/tapecontents.Tpo"; exit 1; fi
rm -f libimagecontents.a
ar cru libimagecontents.a diskcontents-block.o diskcontents-iec.o diskcontents.o imagecontents.o tapecontents.o 
ranlib libimagecontents.a
make[3]: Leaving directory `/home/steve/Desktop/vice-2.1/src/imagecontents'
Making all in fileio
make[3]: Entering directory `/home/steve/Desktop/vice-2.1/src/fileio'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT cbmfile.o -MD -MP -MF ".deps/cbmfile.Tpo" -c -o cbmfile.o cbmfile.c; \
	then mv -f ".deps/cbmfile.Tpo" ".deps/cbmfile.Po"; else rm -f ".deps/cbmfile.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT fileio.o -MD -MP -MF ".deps/fileio.Tpo" -c -o fileio.o fileio.c; \
	then mv -f ".deps/fileio.Tpo" ".deps/fileio.Po"; else rm -f ".deps/fileio.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src    -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT p00.o -MD -MP -MF ".deps/p00.Tpo" -c -o p00.o p00.c; \
	then mv -f ".deps/p00.Tpo" ".deps/p00.Po"; else rm -f ".deps/p00.Tpo"; exit 1; fi
rm -f libfileio.a
ar cru libfileio.a cbmfile.o fileio.o p00.o 
ranlib libfileio.a
make[3]: Leaving directory `/home/steve/Desktop/vice-2.1/src/fileio'
Making all in video
make[3]: Entering directory `/home/steve/Desktop/vice-2.1/src/video'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/raster   --param max-inline-insns-single=600 -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT render1x1.o -MD -MP -MF ".deps/render1x1.Tpo" -c -o render1x1.o render1x1.c; \
	then mv -f ".deps/render1x1.Tpo" ".deps/render1x1.Po"; else rm -f ".deps/render1x1.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/raster   --param max-inline-insns-single=600 -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT render1x1pal.o -MD -MP -MF ".deps/render1x1pal.Tpo" -c -o render1x1pal.o render1x1pal.c; \
	then mv -f ".deps/render1x1pal.Tpo" ".deps/render1x1pal.Po"; else rm -f ".deps/render1x1pal.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/raster   --param max-inline-insns-single=600 -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT render1x2.o -MD -MP -MF ".deps/render1x2.Tpo" -c -o render1x2.o render1x2.c; \
	then mv -f ".deps/render1x2.Tpo" ".deps/render1x2.Po"; else rm -f ".deps/render1x2.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/raster   --param max-inline-insns-single=600 -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT render2x2.o -MD -MP -MF ".deps/render2x2.Tpo" -c -o render2x2.o render2x2.c; \
	then mv -f ".deps/render2x2.Tpo" ".deps/render2x2.Po"; else rm -f ".deps/render2x2.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/raster   --param max-inline-insns-single=600 -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT render2x2pal.o -MD -MP -MF ".deps/render2x2pal.Tpo" -c -o render2x2pal.o render2x2pal.c; \
	then mv -f ".deps/render2x2pal.Tpo" ".deps/render2x2pal.Po"; else rm -f ".deps/render2x2pal.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/raster   --param max-inline-insns-single=600 -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT renderscale2x.o -MD -MP -MF ".deps/renderscale2x.Tpo" -c -o renderscale2x.o renderscale2x.c; \
	then mv -f ".deps/renderscale2x.Tpo" ".deps/renderscale2x.Po"; else rm -f ".deps/renderscale2x.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/raster   --param max-inline-insns-single=600 -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT renderyuv.o -MD -MP -MF ".deps/renderyuv.Tpo" -c -o renderyuv.o renderyuv.c; \
	then mv -f ".deps/renderyuv.Tpo" ".deps/renderyuv.Po"; else rm -f ".deps/renderyuv.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src -I../../src -I../../src/raster   --param max-inline-insns-single=600 -g -O2 -DNO_REGPARM -Wstrict-prototypes -Wall -Winline -MT video-canvas.o -MD -MP -MF ".deps/video-canvas.Tpo" -c -o video-canvas.o video-canvas.c; \
	then mv -f ".deps/video-canvas.Tpo" ".deps/video-canvas.Po"; else rm -f ".deps/video-canvas.Tpo"; exit 1; fi
In file included from ../../src/arch/unix/x11/xaw/videoarch.h:35,
                 from ../../src/arch/unix/videoarch.h:12,
                 from video-canvas.c:39:
../../src/arch/unix/x11/xaw/uiarch.h:33:27: error: X11/Intrinsic.h: No such file or directory
../../src/arch/unix/x11/xaw/uiarch.h:34:28: error: X11/StringDefs.h: No such file or directory
../../src/arch/unix/x11/xaw/uiarch.h:35:24: error: X11/keysym.h: No such file or directory
In file included from ../../src/arch/unix/x11/xaw/videoarch.h:35,
                 from ../../src/arch/unix/videoarch.h:12,
                 from video-canvas.c:39:
../../src/arch/unix/x11/xaw/uiarch.h:43: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ui_window_t’
../../src/arch/unix/x11/xaw/uiarch.h:44: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ui_callback_t’
../../src/arch/unix/x11/xaw/uiarch.h:45: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ui_callback_data_t’
../../src/arch/unix/x11/xaw/uiarch.h:48: error: ‘XK_0’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:49: error: ‘XK_1’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:50: error: ‘XK_2’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:51: error: ‘XK_3’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:52: error: ‘XK_4’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:53: error: ‘XK_5’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:54: error: ‘XK_6’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:55: error: ‘XK_7’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:56: error: ‘XK_8’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:57: error: ‘XK_9’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:58: error: ‘XK_a’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:59: error: ‘XK_b’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:60: error: ‘XK_c’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:61: error: ‘XK_d’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:62: error: ‘XK_e’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:63: error: ‘XK_f’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:64: error: ‘XK_h’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:65: error: ‘XK_i’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:66: error: ‘XK_j’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:67: error: ‘XK_J’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:68: error: ‘XK_k’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:69: error: ‘XK_l’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:70: error: ‘XK_m’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:71: error: ‘XK_n’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:72: error: ‘XK_N’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:73: error: ‘XK_p’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:74: error: ‘XK_q’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:75: error: ‘XK_s’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:76: error: ‘XK_t’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:77: error: ‘XK_u’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:78: error: ‘XK_w’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:79: error: ‘XK_z’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:80: error: ‘XK_F9’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:81: error: ‘XK_F10’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:82: error: ‘XK_F11’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:83: error: ‘XK_F12’ undeclared here (not in a function)
../../src/arch/unix/x11/xaw/uiarch.h:94: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘_ui_top_level’
../../src/arch/unix/x11/xaw/uiarch.h:95: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../src/arch/unix/x11/xaw/uiarch.h:102: error: expected ‘)’ before ‘w’
../../src/arch/unix/x11/xaw/uiarch.h:103: error: expected ‘)’ before ‘w’
../../src/arch/unix/x11/xaw/uiarch.h:104: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ui_create_shell’
../../src/arch/unix/x11/xaw/uiarch.h:106: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ui_create_transient_shell’
../../src/arch/unix/x11/xaw/uiarch.h:107: error: expected ‘)’ before ‘w’
../../src/arch/unix/x11/xaw/uiarch.h:108: error: expected ‘)’ before ‘w’
../../src/arch/unix/x11/xaw/uiarch.h:109: error: expected ‘)’ before ‘w’
In file included from ../../src/arch/unix/videoarch.h:12,
                 from video-canvas.c:39:
../../src/arch/unix/x11/xaw/videoarch.h:40:22: error: X11/Xlib.h: No such file or directory
In file included from ../../src/arch/unix/videoarch.h:12,
                 from video-canvas.c:39:
../../src/arch/unix/x11/xaw/videoarch.h:70: error: expected specifier-qualifier-list before ‘ui_window_t’
../../src/arch/unix/x11/xaw/videoarch.h:110: error: expected ‘)’ before ‘w’
video-canvas.c: In function ‘video_canvas_init’:
video-canvas.c:55: error: ‘video_canvas_t’ has no member named ‘videoconfig’
video-canvas.c:58: error: ‘video_canvas_t’ has no member named ‘draw_buffer’
video-canvas.c:59: error: ‘video_canvas_t’ has no member named ‘viewport’
video-canvas.c:60: error: ‘video_canvas_t’ has no member named ‘geometry’
video-canvas.c: In function ‘video_canvas_shutdown’:
video-canvas.c:70: error: ‘video_canvas_t’ has no member named ‘videoconfig’
video-canvas.c:71: error: ‘video_canvas_t’ has no member named ‘draw_buffer’
video-canvas.c:72: error: ‘video_canvas_t’ has no member named ‘viewport’
video-canvas.c:73: error: ‘video_canvas_t’ has no member named ‘viewport’
video-canvas.c:74: error: ‘video_canvas_t’ has no member named ‘geometry’
video-canvas.c: In function ‘video_canvas_render’:
video-canvas.c:83: error: ‘video_canvas_t’ has no member named ‘viewport’
video-canvas.c:90: error: ‘video_canvas_t’ has no member named ‘videoconfig’
video-canvas.c:90: error: ‘video_canvas_t’ has no member named ‘draw_buffer’
video-canvas.c:92: error: ‘video_canvas_t’ has no member named ‘draw_buffer’
video-canvas.c: In function ‘video_canvas_refresh_all’:
video-canvas.c:106: error: ‘video_canvas_t’ has no member named ‘viewport’
video-canvas.c:107: error: ‘video_canvas_t’ has no member named ‘geometry’
video-canvas.c:115: error: ‘video_canvas_t’ has no member named ‘draw_buffer’
video-canvas.c:115: error: ‘video_canvas_t’ has no member named ‘draw_buffer’
video-canvas.c:117: error: ‘video_canvas_t’ has no member named ‘draw_buffer’
video-canvas.c:117: error: ‘video_canvas_t’ has no member named ‘draw_buffer’
video-canvas.c: In function ‘video_canvas_redraw_size’:
video-canvas.c:124: error: ‘video_canvas_t’ has no member named ‘videoconfig’
video-canvas.c:126: error: ‘video_canvas_t’ has no member named ‘videoconfig’
video-canvas.c:129: error: ‘video_canvas_t’ has no member named ‘draw_buffer’
video-canvas.c:130: error: ‘video_canvas_t’ has no member named ‘draw_buffer’
video-canvas.c:131: error: ‘video_canvas_t’ has no member named ‘draw_buffer’
video-canvas.c:132: error: ‘video_canvas_t’ has no member named ‘draw_buffer’
video-canvas.c: In function ‘video_canvas_palette_set’:
video-canvas.c:146: error: ‘struct video_canvas_s’ has no member named ‘palette’
video-canvas.c:152: error: ‘struct video_canvas_s’ has no member named ‘palette’
make[3]: *** [video-canvas.o] Error 1
make[3]: Leaving directory `/home/steve/Desktop/vice-2.1/src/video'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/steve/Desktop/vice-2.1/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/steve/Desktop/vice-2.1/src'
make: *** [all-recursive] Error 1
steve@Iago:~/Desktop/vice-2.1$

---

### Post by michy99 on 2009-06-03
It looks like you need to add some libraries. Enter```
sudo apt-get install libxt6 libxt-dev libxaw7
```

---

### Post by Yellow Pasque on 2009-06-03
```
sudo apt-get build-dep vice
```

Then:
```
./configure
make
sudo make install
```

---

### Post by trench.me on 2009-06-03
Are you understanding what you are doing as you are being told to do it?

I mean, once you get this setup like you want that's going to be great, but not so much if you don't understand what it is that you did. 

```
man tar
```

and

```
man make
```

... should help you a great deal.

---

