---
title: "PSPP from CVS"
date: 2006-03-19
forum: Education &amp; Science
---

### Post by LadyDoor on 2006-03-19
Hi all,

Here's the thing:  I'm pretty much a total newbie at CVS stuff, so I'm just wondering whether anybody's had any success installing recent versions of PSPP stats software from CVS...when I tried, at the first step the instructions prescribe after downloading it ("make -f Smake"), make runs fine for a little while  and then spits out the following:

```
Don't forget to
  - add "gl/Makefile" to AC_CONFIG_FILES in ./configure.ac,
  - mention "gl" in SUBDIRS in Makefile.am,
  - mention "-I gl/m4" in ACLOCAL_AMFLAGS in Makefile.am,
  - invoke gl_EARLY in ./configure.ac, right after AC_PROG_CC,
  - invoke gl_INIT in ./configure.ac.
autoreconf --install
aclocal: configure.ac: 12: macro `AM_PROG_CC_C_O' not found in library
autoreconf: aclocal failed with exit status: 1
make: *** [all] Error 1

```

I'd like to at least try to install it rather than giving up, because it seems to be more fully-featured than the one in the repositories...however, I do not have the sheer know-how to accomplish this. So any suggestions regarding either how to make it actually install or suggestions regarding other statistical software that can read SPSS files would be much appreciated.

--Door

---

### Post by LadyDoor on 2006-03-21
Don't forget, as always I have abundances of kudos for anybody who wishes to help! Also:  I've discovered some Guru-Points lying around for anybody who comes up with an End-All, Be-All Solution. So if anybody knows how to solve these ./configure problems with ACLOCAL and such, it would be much appreciated! Think of it as a challenge!

--Door

---

### Post by LadyDoor on 2006-03-21
Maybe this will help...here's the full output from "make -f Smake"

```
test -d m4 || mkdir m4
touch m4/Makefile.am
../gnulib/gnulib-tool --import --no-changelog --m4-base=gl/m4 \
        --source-base=gl --lib=libgl --tests-base=tests \
        --import alloca alloca-opt assert c-ctype full-read full-write gethostname getline getlogin_r getopt gettext intprops memcasecmp memchr memcmp
memmem memmove memset progname readlink restrict snprintf stat-macros stdbool stpcpy strcase strcspn strerror strftime strstr strtod strtok_r strtol strtoul unistd vsnprintf xalloc xalloc-die xreadlink xvasprintf
Module list with included dependencies:
  alloca
  alloca-opt
  assert
  c-ctype
  error
  exit
  exitfail
  extensions
  full-read
  full-write
  getdelim
  gethostname
  getline
  getlogin_r
  getopt
  gettext
  gettext-h
  havelib
  intprops
  mbchar
  mbuiter
  memcasecmp
  memchr
  memcmp
  memmem
  memmove
  memset
  minmax
  progname
  readlink
  restrict
  safe-read
  safe-write
  size_max
  snprintf
  ssize_t
 stat-macros
  stdbool
  stpcpy
  strcase
  strcspn
  strerror
  strftime
  strnlen1
  strstr
  strtod
  strtok_r
  strtol
  strtoul
  time_r
  unistd
  vasnprintf
  vasprintf
  vsnprintf
  xalloc
  xalloc-die
  xreadlink
  xsize
  xvasprintf
File list:
  build-aux/config.rpath
  lib/alloca.c
  lib/alloca_.h
  lib/asnprintf.c
  lib/asprintf.c
  lib/c-ctype.c
  lib/c-ctype.h
  lib/error.c
  lib/error.h
  lib/exit.h
  lib/exitfail.c
  lib/exitfail.h
  lib/full-read.c
  lib/full-read.h
  lib/full-write.c
  lib/full-write.h
  lib/getdelim.c
  lib/getdelim.h
  lib/gethostname.c
  lib/getline.c
lib/getline.h
  lib/getlogin_r.c
  lib/getlogin_r.h
  lib/getopt.c
  lib/getopt1.c
  lib/getopt_.h
  lib/getopt_int.h
  lib/gettext.h
  lib/intprops.h
  lib/mbchar.c
  lib/mbchar.h
  lib/mbuiter.h
  lib/memcasecmp.c
  lib/memcasecmp.h
  lib/memchr.c
  lib/memcmp.c
  lib/memmem.c
  lib/memmem.h
  lib/memmove.c
  lib/memset.c
  lib/minmax.h
  lib/printf-args.c
  lib/printf-args.h
  lib/printf-parse.c
  lib/printf-parse.h
  lib/progname.c
  lib/progname.h
  lib/readlink.c
  lib/safe-read.c
  lib/safe-read.h
  lib/safe-write.c
  lib/safe-write.h
  lib/size_max.h
  lib/snprintf.c
  lib/snprintf.h
  lib/stat-macros.h
  lib/stdbool_.h
  lib/stpcpy.c
  lib/stpcpy.h
  lib/strcase.h
  lib/strcasecmp.c
  lib/strcspn.c
  lib/strerror.c
  lib/strftime.c
lib/strftime.h
  lib/strncasecmp.c
  lib/strnlen1.c
  lib/strnlen1.h
  lib/strstr.c
  lib/strstr.h
  lib/strtod.c
  lib/strtok_r.c
  lib/strtok_r.h
  lib/strtol.c
  lib/strtoul.c
  lib/time_r.c
  lib/time_r.h
  lib/vasnprintf.c
  lib/vasnprintf.h
  lib/vasprintf.c
  lib/vasprintf.h
  lib/vsnprintf.c
  lib/vsnprintf.h
  lib/xalloc-die.c
  lib/xalloc.h
  lib/xasprintf.c
  lib/xmalloc.c
  lib/xreadlink.c
  lib/xreadlink.h
  lib/xsize.h
  lib/xvasprintf.c
  lib/xvasprintf.h
  m4/alloca.m4
  m4/assert.m4
  m4/codeset.m4
  m4/eoverflow.m4
  m4/error.m4
  m4/exitfail.m4
  m4/extensions.m4
  m4/getdelim.m4
  m4/gethostname.m4
  m4/getline.m4
  m4/getlogin_r.m4
  m4/getopt.m4
  m4/gettext.m4
  m4/glibc2.m4
  m4/glibc21.m4
  m4/iconv.m4
 m4/intdiv0.m4
  m4/intmax.m4
  m4/intmax_t.m4
  m4/inttypes-pri.m4
  m4/inttypes.m4
  m4/inttypes_h.m4
  m4/isc-posix.m4
  m4/lcmessage.m4
  m4/lib-ld.m4
  m4/lib-link.m4
  m4/lib-prefix.m4
  m4/longdouble.m4
  m4/longlong.m4
  m4/mbchar.m4
  m4/mbiter.m4
  m4/mbrtowc.m4
  m4/mbstate_t.m4
  m4/memcasecmp.m4
  m4/memchr.m4
  m4/memcmp.m4
  m4/memmem.m4
  m4/memmove.m4
  m4/memset.m4
  m4/minmax.m4
  m4/nls.m4
  m4/onceonly_2_57.m4
  m4/po.m4
  m4/printf-posix.m4
  m4/progtest.m4
  m4/readlink.m4
  m4/restrict.m4
  m4/safe-read.m4
  m4/safe-write.m4
  m4/signed.m4
  m4/size_max.m4
  m4/snprintf.m4
  m4/ssize_t.m4
  m4/stat-macros.m4
  m4/stdbool.m4
  m4/stdint_h.m4
  m4/stpcpy.m4
  m4/strcase.m4
  m4/strcspn.m4
  m4/strerror.m4
  m4/strerror_r.m4
  m4/strftime.m4
  m4/strstr.m4
  m4/strtod.m4
  m4/strtok_r.m4
  m4/strtol.m4
  m4/strtoul.m4
  m4/time_r.m4
  m4/tm_gmtoff.m4
  m4/uintmax_t.m4
  m4/ulonglong.m4
  m4/unistd_h.m4
  m4/vasnprintf.m4
  m4/vasprintf.m4
  m4/vsnprintf.m4
  m4/wchar_t.m4
  m4/wint_t.m4
  m4/xalloc.m4
  m4/xreadlink.m4
  m4/xsize.m4
Finished.

You may need to add #include directives for the following .h files.
  #endif
  #if HAVE_MBRTOWC
  #if HAVE_WCHAR_H && HAVE_WCTYPE_H
  #include "c-ctype.h"
  #include "error.h"
  #include "exit.h"
  #include "exitfail.h"
  #include "full-read.h"
  #include "full-write.h"
  #include "getdelim.h"
  #include "getline.h"
  #include "getlogin_r.h"
  #include "gettext.h"
  #include "intprops.h"
  #include "mbchar.h"
  #include "mbuiter.h"
  #include "memcasecmp.h"
  #include "memmem.h"
  #include "minmax.h"
  #include "progname.h"
  #include "safe-read.h"
  #include "safe-write.h"
  #include "size_max.h"
  #include "snprintf.h"
  #include "stat-macros.h"
  #include "stpcpy.h"
  #include "strcase.h"
  #include "strftime.h"
  #include "strnlen1.h"
  #include "strstr.h"
  #include "strtok_r.h"
  #include "time_r.h"
  #include "vasnprintf.h"
  #include "vasprintf.h"
  #include "vsnprintf.h"
  #include "xalloc.h"
  #include "xreadlink.h"
  #include "xsize.h"
  #include "xvasprintf.h"
  #include <alloca.h>
  #include <assert.h>
  #include <getopt.h>
  #include <stdbool.h>
  #include <stdlib.h>
  #include <string.h>
  #include <sys/types.h>
  #include <unistd.h>

Don't forget to
  - add "gl/Makefile" to AC_CONFIG_FILES in ./configure.ac,
  - mention "gl" in SUBDIRS in Makefile.am,
  - mention "-I gl/m4" in ACLOCAL_AMFLAGS in Makefile.am,
  - invoke gl_EARLY in ./configure.ac, right after AC_PROG_CC,
  - invoke gl_INIT in ./configure.ac.
autoreconf --install
aclocal: configure.ac: 12: macro `AM_PROG_CC_C_O' not found in library
autoreconf: aclocal failed with exit status: 1
make: *** [all] Error 1
```

---

