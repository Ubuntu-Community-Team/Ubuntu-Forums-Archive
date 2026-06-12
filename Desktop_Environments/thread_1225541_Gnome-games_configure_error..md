---
title: "Gnome-games configure error."
date: 2009-07-28
forum: Desktop Environments
---

### Post by dragos240 on 2009-07-28
```

./autogen.sh
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.63
checking for automake >= 1.9...
  testing automake-1.11... found 1.11
checking for libtool >= 1.4.3...
  testing libtoolize... found 2.2.6
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.20.4
checking for intltool >= 0.40.4...
  testing intltoolize... found 0.40.6
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.23
checking for gnome-doc-utils >= 0.10.0...
  testing gnome-doc-prepare... found 0.16.1
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running gnome-doc-prepare...
You should update your 'aclocal.m4' by running aclocal.
Putting files in AC_CONFIG_MACRO_DIR, 'm4'.
Running aclocal-1.11...
Running autoconf...
Running autoheader...
Running automake-1.11...
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to disable maintainer-specific portions of Makefiles... yes
checking which games to build... checking whether to enable staging games... 
aisleriot blackjack gnometris gnect gnomine same-gnome mahjongg gtali gnotravex gnotski glines iagno glchess gnobots2 gnibbles gnome-sudoku
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.15... yes
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
checking how to run the C preprocessor... gcc -E
checking whether ln -s works... yes
checking for a sed that does not truncate output... /bin/sed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking how to run the C preprocessor... gcc -E
checking for ranlib... ranlib
checking whether make sets $(MAKE)... (cached) yes
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
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking for sys/types.h... (cached) yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for C99 variable arrays... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for sendmsg... yes
checking for network feature: PF_LOCAL... yes
checking for network feature: SUN_LEN... yes
checking for network feature: msg_controllen... yes
checking for network feature: CMSG_ALIGN... yes
checking for network feature: CMSG_LEN... yes
checking for network feature: CMSG_SPACE... yes
checking for socket in -lsocket... no
checking for gethostbyname in -lnsl... yes
checking winsock2.h usability... no
checking winsock2.h presence... no
checking for winsock2.h... no
checking whether gcc and cc understand -c and -o together... yes
checking for a sed that does not truncate output... (cached) /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking the maximum length of command line arguments... 1966080
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... (cached) ranlib
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
checking if gcc static flag -static works... no
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
checking if g++ static flag -static works... no
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether gcc understands -Wno-sign-compare... yes
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare
checking what language compliance flags to pass to the C compiler... 
checking what warning flags to pass to the C++ compiler... -Wall -Wno-unused -Wshadow -Woverloaded-virtual
checking what language compliance flags to pass to the C++ compiler... 
checking for C99 variadic macros... yes
checking for C99 variable arrays... (cached) yes
checking for C99 initializers... yes
checking for stdint.h... (cached) yes
checking for C99 stdint.h... yes
checking for lsb_release... /usr/bin/lsb_release
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/site-packages
checking for which platform to build... gnome
checking host system type... (cached) i686-pc-linux-gnu
checking for some Win32 platform... no
checking for native Win32... no
checking whether to enable sound support... yes
checking for which sound library to use... libcanberra
checking whether to enable aisleriot/clutter... no
checking for requested card theme formats... svg
checking which card theme to use by default... gnomangelo_bitmap.svg
checking which card theme format to use by default... svg
checking whether card themes installer support is requested... no
checking for GTHREAD... yes
checking for GTK... yes
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for gconftool-2... /usr/bin/gconftool-2
checking for XML... yes
checking for GNOME... yes
checking for RSVG... yes
checking for clutter API version... configure: error: no clutter found

```

I can't find a solution.

---

### Post by dragos240 on 2009-07-29
Bump.

---

### Post by dragos240 on 2009-07-30
BUMP! *sigh*

---

### Post by dragos240 on 2009-08-02
Hello?

---

### Post by dragos240 on 2009-08-03
Please? Can someone help? DESUDESUDESUDESU!!!

---

### Post by asmoore82 on 2009-08-03
I would apt-get *clutter*; especially anything like *clutter*-dev

---

### Post by dragos240 on 2009-08-03
I have everything clutter. I even got clutter from source.

---

### Post by dragos240 on 2009-08-05
Bump

---

### Post by deusmac on 2009-08-10
Same problem here and no idea.

---

### Post by qwerty800 on 2009-08-12
Same here...

Maybe that's a bug...

---

### Post by dragos240 on 2009-08-12
No, i'm compiling this on fedora 11.

---

### Post by qwerty800 on 2009-08-12
Oh, here is the thing!

You need libclutter-gtk!

But wait! If you use the latests version, some of the games already use 9.0! And jaunty only package 8.0!

If you want the latest version of gnome game, you're better to get karmic alpha or, on fedora, the rawhide repos.

---

### Post by qwerty800 on 2009-08-13
Still don't work...

But I think I've got the trick!

```
if test "$need_clutter" = "yes"; then
- CLUTTER_API_VERSION=
- AC_MSG_CHECKING([for clutter API version])
- for API_VERSION in 0.9; do
- PKG_CHECK_EXISTS([clutter-$API_VERSION clutter-gtk-$API_VERSION],
- [CLUTTER_API_VERSION=$API_VERSION; break],[])
- done
- if test -z "$CLUTTER_API_VERSION"; then
- AC_MSG_ERROR([no clutter found])
- fi
- AC_MSG_RESULT([$CLUTTER_API_VERSION])
- AC_SUBST([CLUTTER_API_VERSION])
-
- CLUTTER_REQUIRED=0.9.6
- CLUTTER_GTK_REQUIRED=0.9.2
+ CLUTTER_REQUIRED=1.0.0
+ CLUTTER_GTK_REQUIRED=0.10.2
```

---

### Post by qwerty800 on 2009-08-13
Hell, I don't get it!

Even by compiling clutter 1.0.0 myself, I still get the same error!
I tried to comment those parts (I do have clutter, Configure just don't detect them), but the quantity of text to comment would be too huge!

The buggy part starts arround line 22381.

---

### Post by dragos240 on 2009-08-13
> **qwerty800 said:**
> Hell, I don't get it!

Even by compiling clutter 1.0.0 myself, I still get the same error!
I tried to comment those parts (I do have clutter, Configure just don't detect them), but the quantity of text to comment would be too huge!

The buggy part starts arround line 22381.

Then use a pastebin :D

EDIT: On the occation you don't know what is is, well here ya go:
[http://paste.debian.net/](http://paste.debian.net/)

---

### Post by qwerty800 on 2009-08-13
I removed the lines from 22381 to 22668.

I will probably just screw everything up, but let's wait and see...

EDIT: > configure: error: conditional "HAVE_CLUTTER" was never defined.

I'm going to post on the gnome-games official forum to see if anybody can awnser us.

---

### Post by ants280 on 2010-07-07
Also stumping me.

I have: 
[LIST]
[*]libclutter-1.0-0
[*]libclutter1.0-dev
[*]libclutter-gst-0.10-0
[*]libclutter-gst-0.10-dev
[*]libclutter-gtk-0.10-0
[*]libclutter-gtk-0.10-dev
[/LIST]

installed. Still "checking for clutter API version... configure: error: no clutter found"

---

