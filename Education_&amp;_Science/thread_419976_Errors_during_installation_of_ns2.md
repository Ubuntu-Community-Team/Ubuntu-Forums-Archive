---
title: "Errors during installation of ns2"
date: 2007-04-23
forum: Education &amp; Science
---

### Post by vemulabhanu on 2007-04-23
Hi all

I am new to linux and Im trying to install ns2 on my latop. I got the following error messages once i installed and could not complete the process. Pleases suggest me on how to go from here

============================================================
* Testing for Darwin (OS X) environment
============================================================
============================================================
* Testing for Cygwin environment
============================================================
Cygwin not detected, proceeding with regular install.
============================================================
* Build XGraph-12.1
============================================================
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking if malloc debugging is wanted... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
make: *** No targets specified and no makefile found.  Stop.
Can not create xgraph; But xgraph is an optional package, continuing...
============================================================
* Build CWeb
============================================================
Making cweb
gcc -g   -c -o ctangle.o ctangle.c
common.h:36:19: error: stdio.h: No such file or directory
ctangle.w:882:20: error: ctype.h: No such file or directory
ctangle.w:883:21: error: stdlib.h: No such file or directory
common.h:139: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
common.h:140: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
common.h:183: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
common.h:184: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
common.h:185: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
common.h:186: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
common.h:187: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ctangle.w:75: warning: conflicting types for built-in function ‘strlen’
ctangle.w: In function ‘main’:
ctangle.w:712: warning: incompatible implicit declaration of built-in function ‘sprintf’
ctangle.w:97: warning: incompatible implicit declaration of built-in function ‘printf’
ctangle.w: In function ‘push_level’:
ctangle.w:341: error: ‘NULL’ undeclared (first use in this function)
ctangle.w:341: error: (Each undeclared identifier is reported only once
ctangle.w:341: error: for each function it appears in.)
ctangle.w: In function ‘get_output’:
ctangle.w:402: error: ‘C_file’ undeclared (first use in this function)
ctangle.w:425: warning: incompatible implicit declaration of built-in function ‘printf’
ctangle.w: In function ‘flush_buffer’:
ctangle.w:482: error: ‘C_file’ undeclared (first use in this function)
ctangle.w:484: warning: incompatible implicit declaration of built-in function ‘printf’
ctangle.w:486: error: ‘stdout’ undeclared (first use in this function)
ctangle.w: In function ‘phase_two’:
ctangle.w:541: warning: incompatible implicit declaration of built-in function ‘printf’
ctangle.w:547: warning: incompatible implicit declaration of built-in function ‘printf’
ctangle.w:551: warning: incompatible implicit declaration of built-in function ‘printf’
ctangle.w:554: error: ‘stdout’ undeclared (first use in this function)
ctangle.w:573: error: ‘C_file’ undeclared (first use in this function)
ctangle.w:577: warning: incompatible implicit declaration of built-in function ‘printf’
ctangle.w:561: warning: incompatible implicit declaration of built-in function ‘printf’
ctangle.w: In function ‘output_defs’:
ctangle.w:607: error: ‘NULL’ undeclared (first use in this function)
ctangle.w:612: warning: incompatible implicit declaration of built-in function ‘fprintf’
ctangle.w:612: error: ‘C_file’ undeclared (first use in this function)
ctangle.w: In function ‘out_char’:
ctangle.w:656: error: ‘C_file’ undeclared (first use in this function)
ctangle.w:723: warning: incompatible implicit declaration of built-in function ‘fprintf’
ctangle.w:730: warning: incompatible implicit declaration of built-in function ‘fprintf’
ctangle.w: In function ‘get_next’:
ctangle.w:1033: warning: incompatible implicit declaration of built-in function ‘printf’
ctangle.w:1035: error: ‘stdout’ undeclared (first use in this function)
ctangle.w:1035: warning: incompatible implicit declaration of built-in function ‘fwrite’
ctangle.w:1131: warning: incompatible implicit declaration of built-in function ‘printf’
ctangle.w:1133: warning: incompatible implicit declaration of built-in function ‘fwrite’
ctangle.w: In function ‘scan_section’:
ctangle.w:1357: warning: incompatible implicit declaration of built-in function ‘printf’
ctangle.w:1357: error: ‘stdout’ undeclared (first use in this function)
ctangle.w: In function ‘skip_limbo’:
ctangle.w:1508: warning: incompatible implicit declaration of built-in function ‘sscanf’
ctangle.w: In function ‘print_stats’:
ctangle.w:1527: warning: incompatible implicit declaration of built-in function ‘printf’
make: *** [ctangle.o] Error 1
cweb failed to make, but it's optional
chmod: cannot access `cweave': No such file or directory
chmod: cannot access `ctangle': No such file or directory
ln: creating symbolic link `cweave' to `/home/vemulabhanu/Desktop/MyComputer/ns2/ns-allinone-2.31/cweb/cweave': File exists
ln: creating symbolic link `ctangle' to `/home/vemulabhanu/Desktop/MyComputer/ns2/ns-allinone-2.31/cweb/ctangle': File exists
============================================================
* Build Stanford GraphBase
============================================================
Making sgb
if test -r gb_io.ch; then ctangle gb_io.w gb_io.ch; else ctangle gb_io.w; fi
/bin/sh: ctangle: not found
make: *** [gb_io.c] Error 127
Unable to create sgb library, but it's optional, so continuing...
============================================================
* Build GT-ITM
============================================================
sgb lib not found. gt-itm & sgb2ns could not be installed. Continuing..
============================================================
* Build zlib
============================================================
Checking for gcc...
Building static library libz.a version 1.2.3 with gcc.
Checking for unistd.h... No.
Checking whether to use vs[n]printf() or s[n]printf()... using s[n]printf()
Checking for snprintf() in stdio.h... No.
  WARNING: snprintf() not found, falling back to sprintf(). zlib
  can build but will be open to possible buffer-overflow security
  vulnerabilities.
Checking for return value of sprintf()... No.
  WARNING: apparently sprintf() does not return a value. zlib
  can build but will be open to possible string-format security
  vulnerabilities.
Checking for errno.h... No.
Checking for mmap support... No.
gcc -O3 -DNO_snprintf -DHAS_sprintf_void -DNO_ERRNO_H   -c -o example.o example.c
example.c:8:19: error: stdio.h: No such file or directory
example.c:12:22: error: string.h: No such file or directory
example.c:13:22: error: stdlib.h: No such file or directory
example.c: In function ‘test_compress’:
example.c:64: warning: incompatible implicit declaration of built-in function ‘strlen’
example.c:67: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:67: error: ‘stderr’ undeclared (first use in this function)
example.c:67: error: (Each undeclared identifier is reported only once
example.c:67: error: for each function it appears in.)
example.c:67: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:69: warning: incompatible implicit declaration of built-in function ‘strcpy’
example.c:72: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:72: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:75: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:76: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:78: warning: incompatible implicit declaration of built-in function ‘printf’
example.c: In function ‘test_gzio’:
example.c:94: warning: incompatible implicit declaration of built-in function ‘strlen’
example.c:99: error: ‘NULL’ undeclared (first use in this function)
example.c:100: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:100: error: ‘stderr’ undeclared (first use in this function)
example.c:101: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:105: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:106: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:109: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:110: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:117: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:118: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:120: warning: incompatible implicit declaration of built-in function ‘strcpy’
example.c:123: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:124: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:127: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:128: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:130: warning: incompatible implicit declaration of built-in function ‘printf’
example.c:135: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:137: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:141: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:142: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:146: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:147: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:152: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:153: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:156: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:157: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:159: warning: incompatible implicit declaration of built-in function ‘printf’
example.c: In function ‘test_deflate’:
example.c:175: warning: incompatible implicit declaration of built-in function ‘strlen’
example.c:182: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:182: error: ‘stderr’ undeclared (first use in this function)
example.c:182: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:190: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:190: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:197: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:197: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:201: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:201: warning: incompatible implicit declaration of built-in function ‘exit’
example.c: In function ‘test_inflate’:
example.c:214: warning: incompatible implicit declaration of built-in function ‘strcpy’
example.c:225: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:225: error: ‘stderr’ undeclared (first use in this function)
example.c:225: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:231: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:231: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:235: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:235: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:238: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:239: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:241: warning: incompatible implicit declaration of built-in function ‘printf’
example.c: In function ‘test_large_deflate’:
example.c:260: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:260: error: ‘stderr’ undeclared (first use in this function)
example.c:260: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:271: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:271: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:273: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:274: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:282: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:282: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:289: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:289: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:293: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:294: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:297: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:297: warning: incompatible implicit declaration of built-in function ‘exit’
example.c: In function ‘test_large_inflate’:
example.c:310: warning: incompatible implicit declaration of built-in function ‘strcpy’
example.c:320: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:320: error: ‘stderr’ undeclared (first use in this function)
example.c:320: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:327: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:327: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:331: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:331: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:334: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:335: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:337: warning: incompatible implicit declaration of built-in function ‘printf’
example.c: In function ‘test_flush’:
example.c:350: warning: incompatible implicit declaration of built-in function ‘strlen’
example.c:357: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:357: error: ‘stderr’ undeclared (first use in this function)
example.c:357: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:364: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:364: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:371: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:371: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:374: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:374: warning: incompatible implicit declaration of built-in function ‘exit’
example.c: In function ‘test_sync’:
example.c:389: warning: incompatible implicit declaration of built-in function ‘strcpy’
example.c:399: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:399: error: ‘stderr’ undeclared (first use in this function)
example.c:399: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:405: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:405: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:409: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:409: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:413: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:415: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:418: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:418: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:420: warning: incompatible implicit declaration of built-in function ‘printf’
example.c: In function ‘test_dict_deflate’:
example.c:438: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:438: error: ‘stderr’ undeclared (first use in this function)
example.c:438: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:442: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:442: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:449: warning: incompatible implicit declaration of built-in function ‘strlen’
example.c:453: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:454: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:457: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:457: warning: incompatible implicit declaration of built-in function ‘exit’
example.c: In function ‘test_dict_inflate’:
example.c:470: warning: incompatible implicit declaration of built-in function ‘strcpy’
example.c:480: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:480: error: ‘stderr’ undeclared (first use in this function)
example.c:480: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:490: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:491: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:496: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:496: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:500: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:500: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:503: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:504: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:506: warning: incompatible implicit declaration of built-in function ‘printf’
example.c: In function ‘main’:
example.c:524: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:524: error: ‘stderr’ undeclared (first use in this function)
example.c:525: warning: incompatible implicit declaration of built-in function ‘exit’
example.c:528: warning: incompatible implicit declaration of built-in function ‘fprintf’
example.c:531: warning: incompatible implicit declaration of built-in function ‘printf’
example.c:534: warning: incompatible implicit declaration of built-in function ‘calloc’
example.c:541: warning: incompatible implicit declaration of built-in function ‘exit’
make: *** [example.o] Error 1
Zlib make failed, but it's optional Continue ...
============================================================
* Build tcl8.4.14
============================================================
loading cache ./config.cache
checking whether to use symlinks for manpages... no
checking whether to compress the manpages... no
checking whether to add a package name suffix for the manpages... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
tcl8.3.2 configuration failed! Exiting ...
Tcl is not part of the ns project.  Please see [www.Scriptics.com](www.Scriptics.com)
to see if they have a fix for your platform.

---

### Post by fcastillo on 2007-05-30
I'm having exactly the same error message, i don't know how to install ns2. Please somebody help us :cry:

---

### Post by WW on 2007-06-01
Install the **build-essential** package and try again.
```

sudo apt-get install build-essential

```

---

### Post by squared on 2007-06-05
Did this fix the problem?

---

