---
title: "Grrr ./configure and perl"
date: 2005-10-14
forum: Desktop Environments
---

### Post by LinkRJH on 2005-10-14
So I am trying to install this mud client and having no luck.  I've had to get like 100 dependencies already, but now I'm entirely stuck.

linkrjh@ubuntu:~/kildclient-2.2.2$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for KILDCLIENT... yes
checking for perl... perl
checking for perl module ExtUtils::Embed... ok
checking for perl_construct in -lperl... no
configure: error: You do no have the perl library (-lperl) installed
linkrjh@ubuntu:~/kildclient-2.2.2$ cd
linkrjh@ubuntu:~$ cd kildclient-2.2.2
linkrjh@ubuntu:~/kildclient-2.2.2$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for KILDCLIENT... yes
checking for perl... perl
checking for perl module ExtUtils::Embed... ok
checking for perl_construct in -lperl... no
configure: error: You do no have the perl library (-lperl) installed
linkrjh@ubuntu:~/kildclient-2.2.2$ apt-get install libapache-mod-perl
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
linkrjh@ubuntu:~/kildclient-2.2.2$ sudo apt-get install libapache-mod-perl
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  apache-dev libapache-mod-perl-doc
The following NEW packages will be installed:
  libapache-mod-perl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 489kB of archives.
After unpacking 1311kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe libapache-mod-perl 1.29.0.3-8 [489kB]
Fetched 489kB in 3s (157kB/s)

Preconfiguring packages ...
Selecting previously deselected package libapache-mod-perl.
(Reading database ... 116517 files and directories currently installed.)
Unpacking libapache-mod-perl (from .../libapache-mod-perl_1.29.0.3-8_i386.deb) ...
Setting up libapache-mod-perl (1.29.0.3-8) ...
Replacing config file /etc/apache/modules.conf with new version

linkrjh@ubuntu:~/kildclient-2.2.2$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for KILDCLIENT... yes
checking for perl... perl
checking for perl module ExtUtils::Embed... ok
checking for perl_construct in -lperl... no
configure: error: You do no have the perl library (-lperl) installed
linkrjh@ubuntu:~/kildclient-2.2.2$


I've tried 'apt-get install lperl*' and 'apt get install libapache-mod-perl' but neither of them corrected the problem.

Thanks in advance,

Richard

---

### Post by mlomker on 2005-10-14
> configure: error: You do no have the perl library (-lperl) installed


Why didn't you [download]("http://prdownloads.sourceforge.net/kildclient/kildclient_2.2.2-1_i386.deb?download") the .deb package?  I tried it out and it looks fine to me.

---

### Post by LinkRJH on 2005-10-15
Ahh, perfect.  I didn't think it worked for some reason...thank you.

---

### Post by NoTownKasper on 2008-04-17
Having the exact same problem trying to build the newer kildclient version 2.6.0, and I am not using the version available in the repository because it lacks a feature I want. :D 

kasper@Ubuntu-desktop:~/Downloads/kildclient-2.6.0$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for localtime_r... yes
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
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  pt_BR eo
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for KILDCLIENT... yes
checking for perl... perl
checking for perl module ExtUtils::Embed... ok
checking for perl_construct in -lperl... no
configure: error: You do no have the perl library (-lperl) installed
kasper@Ubuntu-desktop:~/Downloads/kildclient-2.6.0$

Tried the same steps as original poster, with no effect, and building source code isn't my specialty. Any ideas?

---

### Post by NoTownKasper on 2008-04-21
(bump)

No Ideas?

---

