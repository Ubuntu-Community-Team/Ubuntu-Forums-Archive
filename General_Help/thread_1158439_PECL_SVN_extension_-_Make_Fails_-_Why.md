---
title: "PECL SVN extension - Make Fails - Why?"
date: 2009-05-13
forum: General Help
---

### Post by AlexsAntidote on 2009-05-13
Hello,

I am trying to install the PECL SVN extension. I have the latest versions of Apache2, PHP5, Subversion, I have the libsvn-dev and dh-make-php.

All installations were performed through apt-get (after update) using default settings.

I get a make fail after running: sudo pecl install -f svn

here is the output:
```
$ sudo pecl install -f svn
WARNING: failed to download pecl.php.net/svn within preferred state "stable", will instead download version 0.5.0, stability "beta"
downloading svn-0.5.0.tgz ...
Starting to download svn-0.5.0.tgz (23,504 bytes)
........done: 23,504 bytes
4 source files, building
running: phpize
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20060613
Zend Extension Api No:   220060519
 1. Please provide the prefix of Subversion installation : autodetect

1-1, 'all', 'abort', or Enter to continue: 
 1. Please provide the prefix of the APR installation used with Subversion : autodetect

1-1, 'all', 'abort', or Enter to continue: 
building in /var/tmp/pear-build-root/svn-0.5.0
running: /tmp/pear/temp/svn/configure --with-svn --with-svn-apr
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc and cc understand -c and -o together... yes
checking for system library directory... lib
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
checking for PHP extension directory... /usr/lib/php5/20060613+lfs
checking for PHP installed headers prefix... /usr/include/php5
checking for re2c... no
configure: WARNING: You will need re2c 0.12.0 or later if you want to regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for svn support... yes, shared
checking for specifying the location of apr for svn... yes, shared
checking for svn includes... Found libsvn 1.5.4
checking for apr and apr-util... Found apr 1.2.12
libsvn includes: "-I/usr/include/subversion-1 -I/usr/include/apr-1.0 -DLINUX=2 -D_REENTRANT -D_GNU_SOURCE -D_LARGEFILE64_SOURCE"
libsvn ldflags: "-lsvn_client-1 -lsvn_fs-1 -lsvn_repos-1 -lsvn_subr-1 -L/usr/lib -lapr-1"
checking for a sed that does not truncate output... (cached) /bin/sed
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
checking how to run the C preprocessor... gcc -E
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
checking for dlfcn.h... yes
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
checking whether to build static libraries... no
configure: creating ./config.status
config.status: creating config.h
config.status: executing libtool commands
running: make
/bin/bash /var/tmp/pear-build-root/svn-0.5.0/libtool --mode=compile gcc -I/usr/include/subversion-1  -I/usr/include/apr-1.0  -DLINUX=2 -D_REENTRANT -D_GNU_SOURCE -D_LARGEFILE64_SOURCE -I. -I/tmp/pear/temp/svn -DPHP_ATOM_INC -I/var/tmp/pear-build-root/svn-0.5.0/include -I/var/tmp/pear-build-root/svn-0.5.0/main -I/tmp/pear/temp/svn -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -DLINUX=2 -D_REENTRANT -D_GNU_SOURCE -D_LARGEFILE64_SOURCE  -DHAVE_CONFIG_H  -g -O2   -c /tmp/pear/temp/svn/svn.c -o svn.lo
libtool: compile:  gcc -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -DLINUX=2 -D_REENTRANT -D_GNU_SOURCE -D_LARGEFILE64_SOURCE -I. -I/tmp/pear/temp/svn -DPHP_ATOM_INC -I/var/tmp/pear-build-root/svn-0.5.0/include -I/var/tmp/pear-build-root/svn-0.5.0/main -I/tmp/pear/temp/svn -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -DLINUX=2 -D_REENTRANT -D_GNU_SOURCE -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -g -O2 -c /tmp/pear/temp/svn/svn.c  -fPIC -DPIC -o .libs/svn.o
/tmp/pear/temp/svn/svn.c: In function ‘php_svn_handle_error’:
/tmp/pear/temp/svn/svn.c:273: warning: format not a string literal and no format arguments
/bin/bash /var/tmp/pear-build-root/svn-0.5.0/libtool --mode=link gcc -DPHP_ATOM_INC -I/var/tmp/pear-build-root/svn-0.5.0/include -I/var/tmp/pear-build-root/svn-0.5.0/main -I/tmp/pear/temp/svn -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -DLINUX=2 -D_REENTRANT -D_GNU_SOURCE -D_LARGEFILE64_SOURCE  -DHAVE_CONFIG_H  -g -O2   -o svn.la -export-dynamic -avoid-version -prefer-pic -module -rpath /var/tmp/pear-build-root/svn-0.5.0/modules  svn.lo -lsvn_client-1 -lsvn_fs-1 -lsvn_repos-1 -lsvn_subr-1 -lapr-1
libtool: link: gcc -shared  .libs/svn.o   /usr/lib/libsvn_client-1.so -L/usr/lib /usr/lib/libsvn_wc-1.so /usr/lib/libsvn_ra-1.so -lsvn_ra_local-1 -lsvn_ra_svn-1 -lsasl2 -lresolv -lsvn_ra_neon-1 -lneon-gnutls /usr/lib/libsvn_diff-1.so /usr/lib/libsvn_repos-1.so /usr/lib/libsvn_fs-1.so -lsvn_fs_fs-1 -lsvn_fs_base-1 -ldb -lsvn_fs_util-1 /usr/lib/libsvn_delta-1.so /usr/lib/libsvn_subr-1.so /usr/lib/libaprutil-1.so -lldap -llber /usr/lib/libdb-4.6.so -lpq /usr/lib/libmysqlclient_r.so -lnsl -lm /usr/lib/libsqlite3.so /usr/lib/libexpat.so -lz /usr/lib/libapr-1.so -luuid -lrt -lcrypt -lpthread -ldl    -pthread -Wl,-soname -Wl,svn.so -o .libs/svn.so
/usr/bin/ld: cannot find -lsasl2
collect2: ld returned 1 exit status
make: *** [svn.la] Error 1
ERROR: `make' failed

```

any help would be appreciated

---

### Post by AlexsAntidote on 2009-05-14
Perhaps if no one knows the answer could someone suggest a better forum to answer my question?

Thanks!

---

### Post by AlexsAntidote on 2009-05-14
Here's an update...

I tried using lower-level commands to compile the extension manually. I got a make fail again but a different error. Here is the commands and output I used:

```
alex@my-server:~/svn-0.5.0$ phpize
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20060613
Zend Extension Api No:   220060519
alex@my-server:~/svn-0.5.0$ ./configure
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc and cc understand -c and -o together... yes
checking for system library directory... lib
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
checking for PHP extension directory... /usr/lib/php5/20060613+lfs
checking for PHP installed headers prefix... /usr/include/php5
checking for re2c... no
configure: WARNING: You will need re2c 0.12.0 or later if you want to regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for svn support... yes, shared
checking for specifying the location of apr for svn... yes, shared
checking for svn includes... Found libsvn 1.5.4
checking for apr and apr-util... Found apr 1.2.12
libsvn includes: "-I/usr/include/subversion-1 -I/usr/include/apr-1.0 -DLINUX=2 -D_REENTRANT -D_GNU_SOURCE -D_LARGEFILE64_SOURCE"
libsvn ldflags: "-lsvn_client-1 -lsvn_fs-1 -lsvn_repos-1 -lsvn_subr-1 -L/usr/lib -lapr-1"
checking for a sed that does not truncate output... (cached) /bin/sed
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
checking how to run the C preprocessor... gcc -E
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
checking for dlfcn.h... yes
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
checking whether to build static libraries... no
configure: creating ./config.status
config.status: creating config.h
config.status: executing libtool commands
alex@my-server:~/svn-0.5.0$ make
/bin/bash /home/mason/svn-0.5.0/libtool --mode=compile gcc -I/usr/include/subversion-1  -I/usr/include/apr-1.0  -DLINUX=2 -D_REENTRANT -D_GNU_SOURCE -D_LARGEFILE64_SOURCE -I. -I/home/mason/svn-0.5.0 -DPHP_ATOM_INC -I/home/mason/svn-0.5.0/include -I/home/mason/svn-0.5.0/main -I/home/mason/svn-0.5.0 -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -DLINUX=2 -D_REENTRANT -D_GNU_SOURCE -D_LARGEFILE64_SOURCE  -DHAVE_CONFIG_H  -g -O2   -c /home/mason/svn-0.5.0/svn.c -o svn.lo
libtool: compile:  gcc -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -DLINUX=2 -D_REENTRANT -D_GNU_SOURCE -D_LARGEFILE64_SOURCE -I. -I/home/mason/svn-0.5.0 -DPHP_ATOM_INC -I/home/mason/svn-0.5.0/include -I/home/mason/svn-0.5.0/main -I/home/mason/svn-0.5.0 -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -DLINUX=2 -D_REENTRANT -D_GNU_SOURCE -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -g -O2 -c /home/mason/svn-0.5.0/svn.c  -fPIC -DPIC -o .libs/svn.o
/home/mason/svn-0.5.0/svn.c: In function ‘php_svn_handle_error’:
/home/mason/svn-0.5.0/svn.c:273: warning: format not a string literal and no format arguments
/bin/bash /home/mason/svn-0.5.0/libtool --mode=link gcc -DPHP_ATOM_INC -I/home/mason/svn-0.5.0/include -I/home/mason/svn-0.5.0/main -I/home/mason/svn-0.5.0 -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -DLINUX=2 -D_REENTRANT -D_GNU_SOURCE -D_LARGEFILE64_SOURCE  -DHAVE_CONFIG_H  -g -O2   -o svn.la -export-dynamic -avoid-version -prefer-pic -module -rpath /home/mason/svn-0.5.0/modules  svn.lo -lsvn_client-1 -lsvn_fs-1 -lsvn_repos-1 -lsvn_subr-1 -lapr-1
libtool: link: gcc -shared  .libs/svn.o   /usr/lib/libsvn_client-1.so -L/usr/lib /usr/lib/libsvn_wc-1.so /usr/lib/libsvn_ra-1.so -lsvn_ra_local-1 -lsvn_ra_svn-1 -lsasl2 -lresolv -lsvn_ra_neon-1 -lneon-gnutls /usr/lib/libsvn_diff-1.so /usr/lib/libsvn_repos-1.so /usr/lib/libsvn_fs-1.so -lsvn_fs_fs-1 -lsvn_fs_base-1 -ldb -lsvn_fs_util-1 /usr/lib/libsvn_delta-1.so /usr/lib/libsvn_subr-1.so /usr/lib/libaprutil-1.so -lldap -llber /usr/lib/libdb-4.6.so -lpq /usr/lib/libmysqlclient_r.so -lnsl -lm /usr/lib/libsqlite3.so /usr/lib/libexpat.so -lz /usr/lib/libapr-1.so -luuid -lrt -lcrypt -lpthread -ldl    -pthread -Wl,-soname -Wl,svn.so -o .libs/svn.so
/usr/bin/ld: cannot find -lsasl2
collect2: ld returned 1 exit status
make: *** [svn.la] Error 1
```

It looks like I need lsasl2 but I have no idea what package that belongs to. I tried: apt-cache search lsasl2 and got nothing, tried apt-cache search lsas and could only find "likewise-open5-lsass"

Any ideas?

---

### Post by AlexsAntidote on 2009-05-14
OK fixed it... In case anyone else ever searches for this (if they perhaps have the same/similar problem) here is how I fixed it:

I changed my search to:
```
apt-cache search sasl2
``` (instead of lsasl2)

found and installed as follows
```
sudo apt-get install libsasl2-dev libsasl2-modules-ldap
```

then I ran phpize followed by ./configure and make

got the following error:
/usr/bin/ld: cannot find -lneon-gnutls

found what I needed with:
```
apt-cache search neon gnutls
```

installed
```
sudo apt-get install libneon27-gnutls-dev
```

ran:
$ phpize
$ ./configure
$ make

Build Complete!

---

### Post by nerdlinger on 2009-10-21
Thank you very much for this solution!

---

### Post by stormzen on 2010-01-28
Thanks!  ( This came in handy when trying to install rapidsvn .12, as well! )

---

