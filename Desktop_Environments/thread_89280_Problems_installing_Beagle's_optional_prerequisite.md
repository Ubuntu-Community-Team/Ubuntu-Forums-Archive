---
title: "Problems installing Beagle's optional prerequisites"
date: 2005-11-12
forum: Desktop Environments
---

### Post by trevorv on 2005-11-12
First of all; hello! This is my first post here :) 

I am about to install Beagle, but there are a couple of 'optional prerequisites' I would like to install first, namely evolution-sharp, galago, ssindex and pdfinfo. 

When trying to configure evolution-sharp, I get the following error message;
```

checking for evolution-data-server-1.2 >= 1.3.5... Package evolution-data-server-1.2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `evolution-data-server-1.2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'evolution-data-server-1.2' found
checking for evolution-data-server-1.2 >= 1.2.0 evolution-data-server-1.2 < 1.3.0... Package evolution-data-server-1.2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `evolution-data-server-1.2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'evolution-data-server-1.2' found
configure: error: You need evolution-data-server 1.2.x or 1.3.5 or newer

```
How do I go about fixing this? I have the package evolution-data-server installed, but it is version 1.4.1 according to Synaptic.

When trying to configure libgalago, I get the following error message;
```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking whether make sets $(MAKE)... (cached) yes
checking whether ln -s works... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for an ANSI C-conforming const... yes
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
checking for size_t... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

```
How do I sort this one out?

As I read their site, I take it pdfinfo and ssindex are included in xpdf and gnumeric. Is this correct?

And finally, I use Epiphany as my web browser, is there an extension I need for it to index websites?

Thanks a lot for your help, sorry this was so long!

---

### Post by Xian on 2005-11-12
For the first compliation error install the evolution-data-server-dev package. The next error should be resolved with one of the g++ package versions.

---

### Post by trevorv on 2005-11-12
Thanks for your help, I've now installed evolution-sharp and libgalago, and am now trying to install galago-daemon, without much luck. It says it can't find libgalago. Any ideas how I make it find it?

Here's the output;

```

checking for    glib-2.0 >= 2.2.2       gobject-2.0 >= 2.2.2    libgalago >= 0.3.3      dbus-1 >= 0.22  dbus-glib-1 >= 0.22 ... Package libgalago was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgalago.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgalago' found

configure: error: Library requirements (        glib-2.0 >= 2.2.2       gobject-2.0 >= 2.2.2    libgalago >= 0.3.3      dbus-1 >= 0.22  dbus-glib-1 >= 0.22 ) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```

Do I need to adjust this path, and if so, how?

Thanks in advance :)

---

### Post by Xian on 2005-11-12
Find the location of libgalago.pc.

```
$ PKG_CONFIG_PATH=~/path_to_directory
```

---

### Post by trevorv on 2005-11-12
Thanks, I have it all installed now, but have *another* problem.

Beagle searches fine, but is not using either of the programs I installed; i.e, it isn't searching Evolution contacts or displaying people's user status next to searches that bring up IM logs. Evolution isn't either (I installed eds-feed as well).

So I'm assuming this means Galago isn't running, but this doesn't explain why it's not searching Evolution contacts. Is there a command to start it? Or do you think there's something else I need to do?

---

### Post by trevorv on 2005-11-13
Can no-one help? I'd really like to get this working, and any hints are really appreciated!

---

