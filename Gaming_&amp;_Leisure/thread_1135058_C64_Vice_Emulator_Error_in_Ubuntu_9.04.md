---
title: "C64 Vice Emulator Error in Ubuntu 9.04"
date: 2009-04-24
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2009-04-24
Hi. I always install the C64 vice emulator in Synaptic with no problems. I installed it in Ubuntu 9.04 yesterday and below is the full output. What must I do to remedy this? Thanks.

```
Vice terminal output-
~$ x64 
/home/myusername/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/myusername/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/myusername/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Set fontpath: `xset fp+ /usr/lib/vice/fonts'.
*** VICE Version 1.22 ***
 
Welcome to x64, the free portable C64 Emulator.
 
Current VICE team members:
A. Boose, D. Lem, T. Biczo, A. Dehmel, T. Bretz, A. Matthies,
M. Pottendorfer, M. Brenner, S. Trikaliotis, M. van den Heuvel.
 
This is free software with ABSOLUTELY NO WARRANTY.
See the "About VICE" command for more info.
 
X11: Found 24bit visual.
XRandR: XRandR reports current display: 1024x768@56
C64MEM: Error - Couldn't load kernal ROM `kernal'.
Machine initialization failed.

Exiting...
```

---

### Post by Grishka on 2009-04-24
> **Rytron said:**
> Hi. I always install the C64 vice emulator in Synaptic with no problems. I installed it in Ubuntu 9.04 yesterday and below is the full output. What must I do to remedy this? Thanks.

```
Vice terminal output-
~$ x64 
/home/myusername/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/myusername/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/myusername/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Set fontpath: `xset fp+ /usr/lib/vice/fonts'.
*** VICE Version 1.22 ***
 
Welcome to x64, the free portable C64 Emulator.
 
Current VICE team members:
A. Boose, D. Lem, T. Biczo, A. Dehmel, T. Bretz, A. Matthies,
M. Pottendorfer, M. Brenner, S. Trikaliotis, M. van den Heuvel.
 
This is free software with ABSOLUTELY NO WARRANTY.
See the "About VICE" command for more info.
 
X11: Found 24bit visual.
XRandR: XRandR reports current display: 1024x768@56
C64MEM: Error - Couldn't load kernal ROM `kernal'.
Machine initialization failed.

Exiting...
```

it looks like commodore roms are not included. vice in the repos is outdated, anyway. compile 2.1 from source, that'll do it.

---

### Post by Rytron on 2009-04-24
I got the source file but am unable to compile it!

---

### Post by Grishka on 2009-04-24
> **Rytron said:**
> I got the source file but am unable to compile it!

configure with "./configure --enable-fullscreen --enable-gnomeui --enable-ethernet" (enable ethernet only if you want netplay). there are a few extra dependencies, but configure states clearly what it needs. if in doubt, post the output of ./configure here, and I'll tell you what libraries you need.

---

### Post by Rytron on 2009-04-24
> **Grishka said:**
> configure with "./configure --enable-fullscreen --enable-gnomeui --enable-ethernet" (enable ethernet only if you want netplay). there are a few extra dependencies, but configure states clearly what it needs. if in doubt, post the output of ./configure here, and I'll tell you what libraries you need.

Much appreciated Grishka.

Here is the output:

```
$ ./configure --enable-fullscreen --enable-gnomeui --enable-ethernet
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking for XFree86 fullscreen requested...
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
checking for c++... no
checking for g++... no
checking for gcc... gcc
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
```

---

### Post by Grishka on 2009-04-24
here's what it complains about: bison, byacc, flex, gettext... and that's all, because later there's a compiler error. looks like you don't have build-essential installed. install these libraries from synaptic, configure again, and see what it says next.

---

### Post by Rytron on 2009-04-24
> **Grishka said:**
> here's what it complains about: bison, byacc, flex, gettext... and that's all, because later there's a compiler error. looks like you don't have build-essential installed. install these libraries from synaptic, configure again, and see what it says next.

Okay, I installed bison, byacc, flex, gettext & build-essential. I ran ```
./configure --enable-fullscreen --enable-gnomeui --enable-ethernet
``` again and below is the output:



```
$ ./configure --enable-fullscreen --enable-gnomeui --enable-ethernet
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking for XFree86 fullscreen requested...
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
checking for bison... bison -y
checking for flex... flex
checking lex output file root... lex.yy
checking lex library... -lfl
checking whether yytext is a pointer... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for gettext in libc... yes
checking for gettext in libintl... no
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
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
checking zlib.h usability... no
checking zlib.h presence... no
checking for zlib.h... no
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
checking for pcap_open_live in -lpcap... no
checking for pcap_open_live in -lpcap... (cached) no
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
checking png.h usability... no
checking png.h presence... no
checking for png.h... no
checking gif_lib.h usability... no
checking gif_lib.h presence... no
checking for gif_lib.h... no
checking jpeglib.h usability... no
checking jpeglib.h presence... no
checking for jpeglib.h... no
checking for X... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... configure: error: Package requirements (gtk+-2.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by Grishka on 2009-04-24
libgtk2.0-dev and libgtkglext1-dev (for gnome gui), libxxf86vm-dev (for fullscreen), libasound2-dev (for sound), libpng12-dev, libjpeg62-dev, libgif-dev (for png, jpg and gif support), libmp3lame-dev (for sound manipulation). you probably don't need them all, but they'll all add some function to the emulator, if you have them. you need libgtk for sure, though. configure again and see what it says now.
edit: oh yea, you can configure with --with-sdl, if you'd like vice to use sdl for sound, instead of alsa. you'll need libsdl1.2-dev for that, though.

---

### Post by Rytron on 2009-04-24
I think I'll just wait for the Synaptic Vice to be sorted out. This is way too much hassle. If you do get to work, please post it here. Cheers Grishka.

---

### Post by Grishka on 2009-04-24
> **Rytron said:**
> I think I'll just wait for the Synaptic Vice to be sorted out. This is way too much hassle. If you do get to work, please post it here. Cheers Grishka.

too much hassle? o_O vice compiles very easily and without problems. really, you're almost done. I'd make you a debian package, but I'm on hardy now.

---

### Post by Rytron on 2009-04-25
Excellent! I found another method [here]("http://ubuntuforums.org/showthread.php?t=278022"). The Vice C64 emulator is up and running again. Cheers go to [K.Mandla]("http://ubuntuforums.org/member.php?u=71172").

:popcorn:

---

### Post by Grishka on 2009-04-25
> **Rytron said:**
> Excellent! I found another method [here]("http://ubuntuforums.org/showthread.php?t=278022"). The Vice C64 emulator is up and running again. Cheers go to [K.Mandla]("http://ubuntuforums.org/member.php?u=71172").

:popcorn:

cool, but the only difference is that with his method you're getting an uglier interface. :p

---

### Post by Rytron on 2009-04-25
> **Grishka said:**
> cool, but the only difference is that with his method you're getting an uglier interface. :p

I don't mind that. Cheers. :)

---

### Post by el_oscuro on 2009-05-03
Download the official Win32 version of VICE at [http://www.viceteam.org/#download](http://www.viceteam.org/#download), and extract the files to a temporary location.

Run the following script as sudo to copy the required files to /usr/lib/vice:

#/bin/bash
# INSTALL is the location you extracted the downloaded file to.
INSTALL=/install/WinVICE-2.1
cp $INSTALL/DRIVES/* /usr/lib/vice/DRIVES
for x in C128  C64  CBM-II PET PLUS4 VIC20 
do
  cp $INSTALL/$x/* /usr/lib/vice/$x
done

---

### Post by Rytron on 2009-05-04
> **el_oscuro said:**
> Download the official Win32 version of VICE at [http://www.viceteam.org/#download](http://www.viceteam.org/#download), and extract the files to a temporary location.

Run the following script as sudo to copy the required files to /usr/lib/vice:

#/bin/bash
# INSTALL is the location you extracted the downloaded file to.
INSTALL=/install/WinVICE-2.1
cp $INSTALL/DRIVES/* /usr/lib/vice/DRIVES
for x in C128  C64  CBM-II PET PLUS4 VIC20 
do
  cp $INSTALL/$x/* /usr/lib/vice/$x
done


I altered the file as so:
```
#/bin/bash
# INSTALL is the location you extracted the downloaded file to.
INSTALL=/home/rytron/Desktop/vice64installguide/vice-2.1
cp $INSTALL/DRIVES/* /usr/lib/vice/DRIVES
for x in C128 C64 CBM-II PET PLUS4 VIC20
do
cp $INSTALL/$x/* /usr/lib/vice/$x
done
```

I get this error:

```
cp: cannot stat `/home/rytron/Desktop/vice64installguide/vice-2.1/DRIVES/*': No such file or directory
cp: cannot stat `/home/rytron/Desktop/vice64installguide/vice-2.1/C128/*': No such file or directory
cp: cannot stat `/home/rytron/Desktop/vice64installguide/vice-2.1/C64/*': No such file or directory
cp: cannot stat `/home/rytron/Desktop/vice64installguide/vice-2.1/CBM-II/*': No such file or directory
cp: cannot stat `/home/rytron/Desktop/vice64installguide/vice-2.1/PET/*': No such file or directory
cp: cannot stat `/home/rytron/Desktop/vice64installguide/vice-2.1/PLUS4/*': No such file or directory
cp: cannot stat `/home/rytron/Desktop/vice64installguide/vice-2.1/VIC20/*': No such file or directory
```

---

### Post by Grishka on 2009-05-04
alright, I finally got around to making a package for 64-bit jaunty. it's a bit hasty, but should work without hassle. I've put it [here]("http://www.mediafire.com/?myxnmcsy2ch").

---

### Post by Rytron on 2009-05-05
> **Grishka said:**
> alright, I finally got around to making a package for 64-bit jaunty. it's a bit hasty, but should work without hassle. I've put it [here]("http://www.mediafire.com/?myxnmcsy2ch").

Any for 32 bit?

---

### Post by DoktorSeven on 2009-05-05
> **Rytron said:**
> I altered the file as so:
```
#/bin/bash
# INSTALL is the location you extracted the downloaded file to.
INSTALL=/home/rytron/Desktop/vice64installguide/vice-2.1
cp $INSTALL/DRIVES/* /usr/lib/vice/DRIVES
for x in C128 C64 CBM-II PET PLUS4 VIC20
do
cp $INSTALL/$x/* /usr/lib/vice/$x
done
```

I get this error:

```
cp: cannot stat `/home/rytron/Desktop/vice64installguide/vice-2.1/DRIVES/*': No such file or directory
cp: cannot stat `/home/rytron/Desktop/vice64installguide/vice-2.1/C128/*': No such file or directory
cp: cannot stat `/home/rytron/Desktop/vice64installguide/vice-2.1/C64/*': No such file or directory
cp: cannot stat `/home/rytron/Desktop/vice64installguide/vice-2.1/CBM-II/*': No such file or directory
cp: cannot stat `/home/rytron/Desktop/vice64installguide/vice-2.1/PET/*': No such file or directory
cp: cannot stat `/home/rytron/Desktop/vice64installguide/vice-2.1/PLUS4/*': No such file or directory
cp: cannot stat `/home/rytron/Desktop/vice64installguide/vice-2.1/VIC20/*': No such file or directory
```

Looks like you downloaded the source tarball, you just need to modify that INSTALL path to point to the directory where all the C64/C128/VIC20/DRIVES and so on directories are, which in the source tarball is in vice-2.1/data/.  

Basically all you're doing is copying everything from the C64, CBM-II, PET, PLUS4, VIC20, C128 and DRIVES directories into their corresponding directories in /usr/lib/vice/.  Since it's in /usr/lib, you'll need to use sudo to do it.  Putting the proper path in that script should work, but you can always do it manually, something like

[change directory to where you extracted the source or Windows version of Vice, then into wherever the C64 directory is, then:]
sudo cp * /usr/lib/vice/C64/

and similar (into the appropriate directory, running the command above changing the destination path to the appropriate directory)

---

### Post by Grishka on 2009-05-05
> **Rytron said:**
> Any for 32 bit?

[here](http://www.mediafire.com/?senc0ndjfxm) you go, buddy.

---

### Post by Rytron on 2009-05-06
> **Grishka said:**
> [here](http://www.mediafire.com/?senc0ndjfxm) you go, buddy.

Thank you very much Grishka. Your the best. :popcorn:

---

### Post by whoya on 2009-09-23
> **Rytron said:**
> Excellent! I found another method [here]("http://ubuntuforums.org/showthread.php?t=278022"). The Vice C64 emulator is up and running again. Cheers go to [K.Mandla]("http://ubuntuforums.org/member.php?u=71172").

:popcorn:
good find rytron, this guide worked a charm for me.

---

### Post by Rytron on 2009-09-24
I had Vice working but I wanted a better interface.

I installed the [deb file]("http://www.mediafire.com/?senc0ndjfxm") but I get this message now:

```
:~$x64
Reading configuration file `/home/rytron/.vice/vicerc'.
Unknown resource `UseXSync'.
/home/rytron/.vice/vicerc: Unknown resource specification at line 65.
Unknown resource `MITSHM'.
/home/rytron/.vice/vicerc: Unknown resource specification at line 66.
*** VICE Version 2.1 ***
 
Welcome to x64, the free portable C64 Emulator.
 
Current VICE team members:
A. Boose, D. Lem, T. Biczo, A. Dehmel, T. Bretz, A. Matthies,
M. Pottendorfer, M. Brenner, S. Trikaliotis, M. van den Heuvel,
C. Vogelgsang, F. Gennari, M. Kiesel, H. Nuotio, D. Kahlin.
 
This is free software with ABSOLUTELY NO WARRANTY.
See the "About VICE" command for more info.
 
XRandR: XRandR reports current display: 1360x768@50
C64MEM: Error - Couldn't load kernal ROM `kernal'.
Machine initialization failed.

Exiting...
```

Note: I also get the exact same message when I tried to install via the tarbal method with this procedure:

download Vice tarball: [http://vice-emu.sourceforge.net/#download](http://vice-emu.sourceforge.net/#download)
```
sudo aptitude install build-essential libxaw7-dev
tar -xvf vice*
./configure
./configure --disable-realdevice --enable-ethernet --disable-ipv6 --enable-fullscreen --without-esd --without-oss --without-resid --with-x
make
sudo make install
```

---

### Post by Rytron on 2009-09-24
I ran this in terminal:
```
aoss x64dtv
```

I get the emulator to appear. I load a game and have sound but a blank picture.

---

### Post by Grishka on 2009-09-25
the deb package... you had it working well some time ago, right? it may be that a botched configuration file prevents it from working now. try removing ~/.vice/vicerc, or perhaps even the whole ~/.vice directory. it may also be that you've overwritten some installed Vice files with your repeated installation attempts. in that case, try reinstalling Vice. remove it thoroughly beforehand. (sudo make uninstall, and remove the package as well, if you still have it installed.) also, there should be no need to run it with ALSA OSS wrapper. if installed correctly, it should simply run through ALSA.

---

### Post by Rytron on 2009-09-25
> **Grishka said:**
> the deb package... you had it working well some time ago, right? it may be that a botched configuration file prevents it from working now. try removing ~/.vice/vicerc, or perhaps even the whole ~/.vice directory. it may also be that you've overwritten some installed Vice files with your repeated installation attempts. in that case, try reinstalling Vice. remove it thoroughly beforehand. (sudo make uninstall, and remove the package as well, if you still have it installed.) also, there should be no need to run it with ALSA OSS wrapper. if installed correctly, it should simply run through ALSA.

Thank you Grishka for helping me again.

(a) I removed the ~/.vice directory.
(b) I ran sudo make uninstall inside the extracted tarball.
(c) I uninstalled vice from synaptic. I then installed the Vice deb package.

**[COLOR="DarkGreen"]Vice now starts with [COLOR="Indigo"]x64[/COLOR] via the terminal[/COLOR]**
:popcorn:

---

### Post by parovelb on 2010-06-25
Ola!
This is a stupid question. Did I forgot the ROM.
```
Welcome to x64, the free portable C64 Emulator.
 
Current VICE team members:
A. Boose, D. Lem, T. Biczo, A. Dehmel, T. Bretz, A. Matthies,
M. Pottendorfer, M. Brenner, S. Trikaliotis, M. van den Heuvel,
C. Vogelgsang, F. Gennari, M. Kiesel, H. Nuotio, D. Kahlin.
 
This is free software with ABSOLUTELY NO WARRANTY.
See the "About VICE" command for more info.
 
XRandR: XRandR reports current display: 1024x768@61
C64MEM: Error - Couldn't load kernal ROM `kernal'.
Machine initialization failed.

Exiting...

```

---

