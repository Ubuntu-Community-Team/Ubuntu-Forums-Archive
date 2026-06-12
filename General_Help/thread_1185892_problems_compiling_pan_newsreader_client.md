---
title: "problems compiling pan newsreader client"
date: 2009-06-12
forum: General Help
---

### Post by mab1376 on 2009-06-12
when I run ./configure I get this:

I'm running Jaunty AMD64 version.

```

./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking whether time.h and sys/time.h may both be included... yes
checking for localtime_r... yes
checking for tr1/unordered_set... yes
checking whether the compiler implements namespaces... yes
checking whether the compiler has ext/hash_set... yes
checking for gawk... (cached) mawk
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for intltool >= 0.35.5... 0.37.1 found
checking for xgettext... no
checking for msgmerge... no
checking for msgfmt... no
configure: error: GNU gettext tools not found; required for intltool

```

---

### Post by dcstar on 2009-06-13
> **mab1376 said:**
> when I run ./configure I get this:

I'm running Jaunty AMD64 version.

```

........
configure: error: GNU **gettext** tools not found; required for intltool

```

And you have the relevant **gettext** packages(s) installed on your system?

Also, why are you compiling something that is already in the repositories?

---

