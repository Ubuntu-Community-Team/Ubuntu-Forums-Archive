---
title: "issue with php-pear, libglib2.0-dev, and mdbtools"
date: 2008-12-17
forum: General Help
---

### Post by Miata-MS on 2008-12-17
Hello all, I've been banging my head against a wall on this for a while and I'm not sure what the solution is. Apparently not many people try to write php scripts that use MDB databases (wonder why... :p)

libglib2.0-dev php-pear and mdbtools all install just fine, but then when I do :```
sudo pecl install mdbtools
``` I just get the error about mdbtools not found on the default path (see terminal output below). Does anyone have any ideas what I could do to fix this please?

Thank you very much.


```
###@server:~$ sudo apt-get install libglib2.0-dev php-pear mdbtools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libglib2.0-doc
The following NEW packages will be installed:
  libglib2.0-dev mdbtools php-pear
0 upgraded, 3 newly installed, 0 to remove and 48 not upgraded.
Need to get 0B/1296kB of archives.
After this operation, 6349kB of additional disk space will be used.
Selecting previously deselected package libglib2.0-dev.
(Reading database ... 108787 files and directories currently installed.)
Unpacking libglib2.0-dev (from .../libglib2.0-dev_2.18.2-0ubuntu2_i386.deb) ...
Selecting previously deselected package mdbtools.
Unpacking mdbtools (from .../mdbtools_0.5.99.0.6pre1.0.20051109-4_i386.deb) ...
Selecting previously deselected package php-pear.
Unpacking php-pear (from .../php-pear_5.2.6-2ubuntu4_all.deb) ...
Processing triggers for man-db ...
Setting up libglib2.0-dev (2.18.2-0ubuntu2) ...
Setting up mdbtools (0.5.99.0.6pre1.0.20051109-4) ...
Setting up php-pear (5.2.6-2ubuntu4) ...
###@server:~$ sudo pecl install mdbtools
downloading mdbtools-1.0.0.tgz ...
Starting to download mdbtools-1.0.0.tgz (8,783 bytes)
.....done: 8,783 bytes
5 source files, building
running: phpize
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20060613
Zend Extension Api No:   220060519
 1. mdbtools installation directory? : autodetect

1-1, 'all', 'abort', or Enter to continue: 
building in /var/tmp/pear-build-root/mdbtools-1.0.0
running: /tmp/pear/temp/mdbtools/configure --with-mdbtools
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
checking mdbtools installation prefix... yes, shared
checking for pkg-config... /usr/bin/pkg-config
checking for mdbtools in default path... configure: error: not found
ERROR: `/tmp/pear/temp/mdbtools/configure --with-mdbtools' failed
###@server:~$ 
```

---

### Post by yukisan on 2009-06-03
Download mdbtools from [http://sourceforge.net/projects/mdbtools/](http://sourceforge.net/projects/mdbtools/), copy to server, configure, build & install, then run the pecl command

---

### Post by oneliner on 2010-10-13
install mdbtools-dev package and try again, this worked for me

---

