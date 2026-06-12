---
title: "compiling / obtaining gtkpod-aac"
date: 2005-11-12
forum: Desktop Environments
---

### Post by Steel3 on 2005-11-12
Hey all,

I apologize if this has been posted before.  I'd like to use gtkpod-aac to organize a bunch of files that one of my roommates on a mac loaned me, but I haven't found a package for it in universe, backports, and such and I haven't been able to install it from any debs that I've come across.  I downloaded the source and satisfied all of the dependencies, but when i run configure I still don't have mp4v2 available or whatever so it says I can't compile it with aac support.  Any suggestions?

---

### Post by Ampersand on 2005-11-12
Make sure you've got the libmp4v2-dev package (available through apt).

---

### Post by Steel3 on 2005-11-12
[QUOTE=Ampersand]Make sure you've got the libmp4v2-dev package (available through apt).[/QUOTE]

Yup, I had that installed, but for some reason it wasn't picking that up.  Here's the output I get at the end:

Configuration for gtkpod 0.94.0 :
--------------------------------

 Host System Type .....: i686-pc-linux-gnu
 Install path .........: /usr/local
 Preprocessor .........: gcc
 Compiler .............: gcc -g -O2 -Wall -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libglade-2.0 -I/usr/include/libxml2
 Linker ...............: gcc  -lmp4v2 -lid3tag  -pthread -Wl,--export-dynamic -lgthread-2.0 -lglade-2.0 -lgtk-x11-2.0 -lxml2 -lz -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXfixes -lpango-1.0 -lcairo -lXrender -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
 GTK2 version .........: 2.8.6
 GLib2/GThread version : 2.8.3
 id3tag lib ...........: yes
 mp4v2 ................: *** no -- will build without aac support
 NLS/gettext ..........: yes

 Now type 'make' to build gtkpod 0.94.0,
 and then 'make install' for installation.

---

### Post by Remmelas on 2005-11-13
do ./configure --help
sometimes support for some things has to be specifically turned on

---

### Post by Steel3 on 2005-11-13
[QUOTE=Remmelas]do ./configure --help
sometimes support for some things has to be specifically turned on[/QUOTE]

I read it over, and tried "./configure --enable-mp4v2" (I'm not sure if that's the right syntax or the way to do it or whatever), and it didn't look like my output changed -- I think it just can't find whatever it is that its looking for.  Here's the whole thing:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc option to accept ANSI C... none needed
checking for pkg-config... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE_CFLAGS... -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libglade-2.0 -I/usr/include/libxml2
checking for PACKAGE_LIBS... -pthread -Wl,--export-dynamic -lgthread-2.0 -lglade-2.0 -lgtk-x11-2.0 -lxml2 -lz -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXfixes -lpango-1.0 -lcairo -lXrender -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
checking for flex... no
checking for lex... no
checking for yywrap in -lfl... no
checking for yywrap in -ll... no
checking for mount... /bin/mount
checking for umount... /bin/umount
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  de fr he it ja sv
checking for getopt_long_only... yes
checking for getopt_long_only... (cached) yes
checking for flock... yes
checking for statvfs... yes
checking for id3_frame_field in -lid3tag... yes
checking for library containing MP4FileInfo... -lmp4v2
checking mp4.h usability... no
checking mp4.h presence... no
checking for mp4.h... no
*** mp4.h cannot be found. Check your mp4v2 installation.
checking for library containing bind... none required
checking linux/cdrom.h usability... yes
checking linux/cdrom.h presence... yes
checking for linux/cdrom.h... yes
checking scsi/sg.h usability... yes
checking scsi/sg.h presence... yes
checking for scsi/sg.h... yes
checking scsi/scsi.h usability... yes
checking scsi/scsi.h presence... yes
checking for scsi/scsi.h... yes
checking scsi/scsi_ioctl.h usability... yes
checking scsi/scsi_ioctl.h presence... yes
checking for scsi/scsi_ioctl.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating scripts/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands

Configuration for gtkpod 0.94.0 :
--------------------------------

 Host System Type .....: i686-pc-linux-gnu
 Install path .........: /usr/local
 Preprocessor .........: gcc
 Compiler .............: gcc -g -O2 -Wall -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libglade-2.0 -I/usr/include/libxml2
 Linker ...............: gcc  -lmp4v2 -lid3tag  -pthread -Wl,--export-dynamic -lgthread-2.0 -lglade-2.0 -lgtk-x11-2.0 -lxml2 -lz -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXfixes -lpango-1.0 -lcairo -lXrender -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
 GTK2 version .........: 2.8.6
 GLib2/GThread version : 2.8.3
 id3tag lib ...........: yes
 mp4v2 ................: *** no -- will build without aac support
 NLS/gettext ..........: yes

 Now type 'make' to build gtkpod 0.94.0,
 and then 'make install' for installation.

---

### Post by Remmelas on 2005-11-14
try
CPPFLAGS=-I/path/to/mp4.h's/directory ./configure
I can't even find gtkpod-aac to download and try to compile myself, so, I'm just shooting something out here that's worked for me in the past with similar problems.

---

### Post by gk_jam on 2005-11-20
I'm trying to compile gtkpod with aac support as well, since nearly all the files on my Ipod are m4a. Anyway, I've reached this exact point and am getting the same error. Funny thing is that when I check synaptic both libmp4v2-0 and libmp4v2-dev are installed.

UPDATE: The ./configure output shows it looking for this mp4.h file and not finding it. However this file exists in /usr/include. Any ideas?

---

### Post by gk_jam on 2005-11-21
[QUOTE=Remmelas]try
CPPFLAGS=-I/path/to/mp4.h's/directory ./configure
I can't even find gtkpod-aac to download and try to compile myself, so, I'm just shooting something out here that's worked for me in the past with similar problems.[/QUOTE]

Just tried this, didn't work. Here's the end of the output:

```

<snip>
checking for library containing MP4FileInfo... -lmp4v2
checking mp4.h usability... no
checking mp4.h presence... no
checking for mp4.h... no
*** mp4.h cannot be found. Check your mp4v2 installation.
checking for library containing bind... none required
checking linux/cdrom.h usability... yes
checking linux/cdrom.h presence... yes
checking for linux/cdrom.h... yes
checking scsi/sg.h usability... yes
checking scsi/sg.h presence... yes
checking for scsi/sg.h... yes
checking scsi/scsi.h usability... yes
checking scsi/scsi.h presence... yes
checking for scsi/scsi.h... yes
checking scsi/scsi_ioctl.h usability... yes
checking scsi/scsi_ioctl.h presence... yes
checking for scsi/scsi_ioctl.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating scripts/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands

Configuration for gtkpod 0.94.0 :
--------------------------------

 Host System Type .....: i686-pc-linux-gnu
 Install path .........: /usr/local
 Preprocessor .........: gcc -I/usr/include
 Compiler .............: gcc -g -O2 -Wall -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libglade-2.0 -I/usr/include/libxml2
 Linker ...............: gcc  -lmp4v2 -lid3tag  -pthread -Wl,--export-dynamic -lgthread-2.0 -lglade-2.0 -lgtk-x11-2.0 -lxml2 -lz -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXfixes -lpango-1.0 -lcairo -lXrender -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
 GTK2 version .........: 2.8.6
 GLib2/GThread version : 2.8.3
 id3tag lib ...........: yes
 mp4v2 ................: *** no -- will build without aac support
 NLS/gettext ..........: yes

```

The preprocessor is including /usr/include, **which contains the mp4.h header file!**. Also, the output log says it sees lmp4v2, but not the mp4.h header. I'm new to both Linux and Ubuntu, but this seems so weird. Anyone got a line on solving this??

---

### Post by JLTB on 2005-11-21
I'm having this exact same problem!

All my poor m4a's are usless to me now :-( (on my iPod at least).  Maybe somebody goofed when they packed the mp4v2 package? (complete shot in the dark, i'm totally talking out of my ass here).

Sigh, hopefully somebody finds a solution soon.  I'll keep looking.

---

### Post by gk_jam on 2005-11-21
[QUOTE=JLTB]I'm having this exact same problem!

All my poor m4a's are usless to me now :-( (on my iPod at least).  Maybe somebody goofed when they packed the mp4v2 package? (complete shot in the dark, i'm totally talking out of my ass here).

Sigh, hopefully somebody finds a solution soon.  I'll keep looking.[/QUOTE]

Maybe the mp4.h file has some illegal characters/formatting/etc. I can't imagine any other reason why when configuring it would be able to find other header files in the same directory (and it does given the output) but not this one. I don't know c, so I can't tell if the file is illegal.

---

### Post by RAOF on 2005-11-21
It's possible that it's looking for mp4.h under some subdirectory, and mp4.h is actually in /include.  In that case, in the source somewhere would be something like:
```
#include <mp4v2/mp4.h>
```

That's really just clutching at straws, though.

---

### Post by JLTB on 2005-11-22
That's the pertinant part of my config.log.  It's all gibberish to me though (aka, I have work in the morning and don't care to scratch my head right now...).

Maybe somebody can make some sense of this.  I'm no compiler wizard.

```

configure:7173: checking mp4.h usability
configure:7185: gcc -c -g -O2 -Wall  conftest.c >&5
In file included from /usr/include/mpeg4ip.h:28,
                 from /usr/include/mp4.h:27,
                 from conftest.c:69:
/usr/include/systems.h:34:20: error: config.h: No such file or directory
In file included from /usr/include/mpeg4ip.h:28,
                 from /usr/include/mp4.h:27,
                 from conftest.c:69:
/usr/include/systems.h:248: error: syntax error before '__extension__'
/usr/include/systems.h:248: error: syntax error before '&&' token
configure:7191: $? = 1
configure: failed program was:
| /* confdefs.h.  */
|
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "gtkpod"
| #define VERSION "0.94.0"
| #define GETTEXT_PACKAGE "gtkpod"
| #define ITDB_USE_ABBREV 1
| #define YYTEXT_POINTER 1
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_LC_MESSAGES 1
| #define HAVE_BIND_TEXTDOMAIN_CODESET 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define ENABLE_NLS 1
| #define HAVE_GETOPT_LONG_ONLY 1
| #define HAVE_GETOPT_LONG_ONLY 1
| #define HAVE_FLOCK 1
| #define HAVE_STATVFS 1
| #define HAVE_LIBID3TAG 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #if HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #if HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #if STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # if HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #if HAVE_STRING_H
| # if !STDC_HEADERS && HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #if HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #if HAVE_INTTYPES_H
| # include <inttypes.h>
| #else
| # if HAVE_STDINT_H
| #  include <stdint.h>
| # endif
| #endif
| #if HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <mp4.h>
configure:7213: result: no
configure:7217: checking mp4.h presence
configure:7227: gcc -E  conftest.c
In file included from /usr/include/mpeg4ip.h:28,
                 from /usr/include/mp4.h:27,
                 from conftest.c:35:
/usr/include/systems.h:34:20: error: config.h: No such file or directory
configure:7233: $? = 1
configure: failed program was:
| /* confdefs.h.  */
|
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "gtkpod"
| #define VERSION "0.94.0"
| #define GETTEXT_PACKAGE "gtkpod"
| #define ITDB_USE_ABBREV 1
| #define YYTEXT_POINTER 1
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_LOCALE_H 1
| #define HAVE_LC_MESSAGES 1
| #define HAVE_BIND_TEXTDOMAIN_CODESET 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define ENABLE_NLS 1
| #define HAVE_GETOPT_LONG_ONLY 1
| #define HAVE_GETOPT_LONG_ONLY 1
| #define HAVE_FLOCK 1
| #define HAVE_STATVFS 1
| #define HAVE_LIBID3TAG 1
| /* end confdefs.h.  */
| #include <mp4.h>
configure:7253: result: no
configure:7288: checking for mp4.h
configure:7295: result: no

```

---

### Post by gk_jam on 2005-11-22
Ok, I found a line elsewhere on the net that might shed some light here. Apparently, according to [this post]("http://www.linuxquestions.org/questions/history/277034") on linuxquestions.org, gtkpod does not like the mp4.h file that comes with faad2, which is the version of the mp4v2 lib that is in the repository. So the answer is apparently to use the mp4v2 lib (and mp4.h) from mpeg4ip.

Now [http://clug.net.nz/index.php/IpodSupportUnderLinux]("http://clug.net.nz/index.php/IpodSupportUnderLinux") provides a description on how to compile the relevant part of mpeg4ip (ie the mp4v2 lib) from source. It was written for mpeg4ip version 1.3, but the latest version is 1.4.1, which leads to some minor differences (eg. the file mpeg4ip_version.h referenced in that page isn't to be found in the new version). This looks like it might be the answer, but I'm running into trouble when trying to use the "make" command. I am getting this error:

make: *** No targets.  Stop.

Apparently this means no targets are defined in the makefile, but i don't really know what that means, being new to Linux. So, if anyone can tell me what this "no targets" error usually means, that would be great. Also, if someone manages to compile mpeg4ip and thus get the right mp4v2 library for gtkpod, please let me know. Thanks.

---

### Post by gk_jam on 2005-11-22
More updates. I managed to compile the libmp4v2 from mpeg4ip, and it nicely placed its mp4.h file in /usr/local/include.

Well, proceeded to go to the gtkpod src and try the following:

"CPPFLAGS=-I/usr/local/include ./configure"
 
and in the output...

```
 mp4v2 ................: *** no -- will build without aac support
```

](*,)   :cry:

---

### Post by kennethb on 2005-11-23
I'm using Breezy (5.10). Why isn't 'gtkpod' available to install from the Synaptic Package Manager? Is it not stable enough? I'd like to use my iPod with my Ubuntu laptop if possible.

---

### Post by gk_jam on 2005-11-23
[QUOTE=kennethb]I'm using Breezy (5.10). Why isn't 'gtkpod' available to install from the Synaptic Package Manager? Is it not stable enough? I'd like to use my iPod with my Ubuntu laptop if possible.[/QUOTE]

gtkpod is available from synaptic. However, it does not come with aac support (won't handle tags for aac files). The problems in this thread arise from trying to compile gtkpod with aac support. If you don't require that, then you should be good to go using the version obtained through synaptic.

---

### Post by kennethb on 2005-11-23
[QUOTE=gk_jam]gtkpod is available from synaptic. However, it does not come with aac support (won't handle tags for aac files). The problems in this thread arise from trying to compile gtkpod with aac support. If you don't require that, then you should be good to go using the version obtained through synaptic.[/QUOTE]

I just did a search for 'gtkpod' in synaptic and it was not there. Is it under a different name in synaptic?

---

### Post by gk_jam on 2005-11-23
You probably don't have the universe repository enabled. Try this:

sudo gedit /etc/apt/sources.list

and uncomment the line (delete the "# " at the start) that looks like this:
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse

it may just look like
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main

in which case you can go ahead and add "restricted multiverse" to open up those repositories as well.

Save the file and then open synaptic and you should find gtkpod.

--------

Now, as for gtkpod-aac, I tapped out when trying to compile it, but Christian Marillat has put up a version in the debian-marillat repositories, so I installed it using them.

Just add
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sid main

to /etc/apt/sources.list, and then install gtkpod-aac with apt-get or synaptic. You might want to remove the debian-marillat repository from sources.list after installing, as it may cause issues down the line if just left there. Of course, that repository and programs in it are completely unsupported by Ubuntu.

---

### Post by kennethb on 2005-11-23
[QUOTE=gk_jam]You probably don't have the universe repository enabled. Try this:

sudo gedit /etc/apt/sources.list

and uncomment the line (delete the "# " at the start) that looks like this:
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse

it may just look like
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main

in which case you can go ahead and add "restricted multiverse" to open up those repositories as well.

Save the file and then open synaptic and you should find gtkpod.

--------
[/QUOTE]

When I try that, I get an error message when I launch synaptic; the error message says it can't locate some files. Then, when I search in synaptic, it still does not find 'gtkpod'.

Here is what my  /etc/apt/sources.list file contains:

----------------------------------------------------------------------------------------------------------------------------
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
-------------------------------------------------------------------------------------------------------

---

### Post by gk_jam on 2005-11-23
Try this:

Uncomment the line below by removing the #:
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

save the file and open synaptic, it will give you an error on startup. Click the reload button to let it load the new repository. You should now be able to find gtkpod, and should have no further errors when you close and reopen synaptic.

Post here if there are still problems.

---

### Post by MikeMay on 2005-12-10
Well ...
back to the topic ... I have the same problem ...
./configure generates the output:
```
checking for library containing MP4FileInfo... -lmp4v2
checking mp4.h usability... no
checking mp4.h presence... no
checking for mp4.h... no
*** mp4.h cannot be found. Check your mp4v2 installation.
...
 mp4v2 ................: *** no -- will build without aac support
```

Did anybody find a solution?

---

### Post by gk_jam on 2005-12-12
[QUOTE=MikeMay]Well ...
back to the topic ... I have the same problem ...
./configure generates the output:
```
checking for library containing MP4FileInfo... -lmp4v2
checking mp4.h usability... no
checking mp4.h presence... no
checking for mp4.h... no
*** mp4.h cannot be found. Check your mp4v2 installation.
...
 mp4v2 ................: *** no -- will build without aac support
```

Did anybody find a solution?[/QUOTE]

Sort of, you don't have to compile it yourself...cf. my earlier post:

> 
Now, as for gtkpod-aac, I tapped out when trying to compile it, but Christian Marillat has put up a version in the debian-marillat repositories, so I installed it using them.

Just add
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sid main

to /etc/apt/sources.list, and then install gtkpod-aac with apt-get or synaptic. You might want to remove the debian-marillat repository from sources.list after installing, as it may cause issues down the line if just left there. Of course, that repository and programs in it are completely unsupported by Ubuntu.


---

### Post by uopjohnson on 2005-12-16
Well what I did was build mp4v2 from source as well and then everything worked.
Here are my steps:
```

sudo apt-get remove gtkpod libmp4v2-0
sudo apt-get build-dep libmp4v2-0

```
download and untar libmp4v2-0
```

./autogen.sh  <-- important
make
sudo make install

```
you may get an error during autogen.sh that you need to install some stuff.  I was able to get it all with apt-get... I'm not sure why these things don't come up in build-dep, but I think it is because the autogen.sh builds a bunch of other stuff as well as libmp4
if that goes well then you should be able to build gtkpod 
```

./configure
make
sudo make install

```
At the end of ./configure you should now see that it is being built with mp4v2 support and now everything is gravy!  
oh one more thing for some reason ldconfig (which loads shared libraries) was not looking in /usr/local/lib which is where libmp4v2 got put.  You may need to edit /etc/ld.so.conf and add /usr/local/lib so that it will be searched.  then run
```
sudo /sbin/ldconfig
```
to get everything in place.  You will know if this step is necessary because gtkpod will not start and wll give the error
"gtkpod: error while loading shared libraries: libmp4v2.so.0"
Hope that helps someone.

---

### Post by chestnut1969 on 2006-01-03
Hi

Were can the source code re: 

"download and untar libmp4v2-0"

be found? I cannot find by Googling?

Thank you

---

### Post by vikrant82 on 2007-07-24
apt-get source...
Do enable source repositories!

---

### Post by vikrant82 on 2007-07-24
Hmm, rather get libmp4v2-1.5.0.1.tar.bz2  from [http://resare.com/libmp4v2/dist/](http://resare.com/libmp4v2/dist/)
Build this and gtkpod detects mp4.h.
And ya also do ldconfig -v after building libmp4v2

---

### Post by vikrant82 on 2007-07-24
Just to sum up for other's help... 

To build gtkpod 99.10 with MP4 support.

You will have to install libgpod-0.5.2[build from source] but i propose not to remove old version. [As else, some other ipod compatible apps start shouting. [cannot find libgpod.so.1 etc.. OR build them too from source]

Install other needed libraries from normal repos [libcurl etc depending upon what features you need ..], however libmp4v2-dev doesnt make gtkpod stop crying about having not able to find libmp4v2. Keeps complaining " checking for library containing MP4GetMetadataGrouping... no "

So get libmp4v2-1.5.0.1.tar.bz2 from [http://resare.com/libmp4v2/dist/](http://resare.com/libmp4v2/dist/)

That's it! :)

---

### Post by gnychis on 2007-08-31
> **vikrant82 said:**
> Hmm, rather get libmp4v2-1.5.0.1.tar.bz2  from [http://resare.com/libmp4v2/dist/](http://resare.com/libmp4v2/dist/)
Build this and gtkpod detects mp4.h.
And ya also do ldconfig -v after building libmp4v2

just wanted to report that this worked perfectly for me

---

### Post by danwood76 on 2007-11-21
Yeah this worked perfectly!
Ive been trying for days to compile this,
Thanks a lot!

The gtkpod-acc in the synaptic repository is broken (it doesnt have the aac support) why is it still up there?

regards,
Danny

---

### Post by alexef on 2007-11-26
> **vikrant82 said:**
> Just to sum up for other's help... 

To build gtkpod 99.10 with MP4 support.

You will have to install libgpod-0.5.2[build from source] but i propose not to remove old version. [As else, some other ipod compatible apps start shouting. [cannot find libgpod.so.1 etc.. OR build them too from source]

Install other needed libraries from normal repos [libcurl etc depending upon what features you need ..], however libmp4v2-dev doesnt make gtkpod stop crying about having not able to find libmp4v2. Keeps complaining " checking for library containing MP4GetMetadataGrouping... no "

So get libmp4v2-1.5.0.1.tar.bz2 from [http://resare.com/libmp4v2/dist/](http://resare.com/libmp4v2/dist/)

That's it! :)

As  a small completion, after downloading libmp4v2-1.5.0.1.tar.bz2 I had to 
```
./configure 
make 
make install
```
 it, and then I could build gtkpod.

Thank you very much.

---

