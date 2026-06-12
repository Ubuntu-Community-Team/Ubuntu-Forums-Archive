---
title: "problem installing xsupplicant"
date: 2006-04-19
forum: Desktop Environments
---

### Post by nishoba on 2006-04-19
im trying to instal xsupplicant 1.2.4.

but when i run ```
sudo ./configure
```i get error:
```
checking for iwlib.h... yes
checking iwlib version... 3 params
checking for CRYPTO_new_ex_data in -lcrypto... no
configure: error: library 'crypto' is required for Open1x

```

what library do i need to install? or what to do?

thx

---

### Post by croak77 on 2006-04-19
I'll guess libcrypto++-dev. Not sure though.

---

### Post by nishoba on 2006-04-20
ok. i installed a lot of ubuntu packages. and i thing that ./config works now
i get the next result:
```
...
checking for CRYPTO_new_ex_data in -lcrypto... yes
checking for SSL_library_init in -lssl... yes
checking openssl/ssl.h usability... yes
checking openssl/ssl.h presence... yes
checking for openssl/ssl.h... yes
checking openssl/err.h usability... yes
checking openssl/err.h presence... yes
checking for openssl/err.h... yes
checking for native frame interface... linux
checking for procfs support... okay
!! Not building MADWIFI WPA support !!
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating tools/Makefile
config.status: creating doc/Makefile
config.status: creating etc/Makefile
config.status: creating drivers/Makefile
config.status: creating tools/config-parser/Makefile
config.status: creating tools/ntpwdhash/Makefile
config.status: creating gui_tools/Makefile
config.status: creating gui_tools/cli/Makefile
config.status: creating gui_tools/cli/xsup_set_pwd/Makefile
config.status: creating gui_tools/cli/xsup_monitor/Makefile
config.status: creating gui_tools/cli/xsup_get_state/Makefile
config.status: creating lib/Makefile
config.status: creating lib/libxsupgui/Makefile
config.status: creating lib/libxsupconfig/Makefile
config.status: creating lib/libxsupconfwrite/Makefile
config.status: creating lib/libxsupconfcheck/Makefile
config.status: executing depfiles commands

```
but when i try to make it:
```
...
make[3]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_set_pwd'
Making all in xsup_monitor
make[3]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_monitor'
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"xsupplicant\" -DVERSION=\"1.2.2\" -DYYTEXT_POINTER=1 -DLILENDIAN=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DNO_PWD_RESET=1 -DOPENSSL_NO_KRB5=1 -DLINUX=1 -DHAVE_LIBCRYPTO=1 -DHAVE_LIBSSL=1 -DLINUX_FRAMER=1   -I. -I.     -g -O2 -Wall  -c xsup_monitor.c
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"xsupplicant\" -DVERSION=\"1.2.2\" -DYYTEXT_POINTER=1 -DLILENDIAN=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DNO_PWD_RESET=1 -DOPENSSL_NO_KRB5=1 -DLINUX=1 -DHAVE_LIBCRYPTO=1 -DHAVE_LIBSSL=1 -DLINUX_FRAMER=1   -I. -I.     -g -O2 -Wall  -c -o gui_interface.o `test -f '../../common/gui_interface.c' || echo './'`../../common/gui_interface.c
gcc  -g -O2 -Wall    -o xsup_monitor  xsup_monitor.o gui_interface.o  -lfl -liw -lm -lssl -lcrypto
make[3]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_monitor'
Making all in xsup_get_state
make[3]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_get_state'
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"xsupplicant\" -DVERSION=\"1.2.2\" -DYYTEXT_POINTER=1 -DLILENDIAN=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DNO_PWD_RESET=1 -DOPENSSL_NO_KRB5=1 -DLINUX=1 -DHAVE_LIBCRYPTO=1 -DHAVE_LIBSSL=1 -DLINUX_FRAMER=1   -I. -I.     -g -O2 -Wall  -c xsup_get_state.c
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"xsupplicant\" -DVERSION=\"1.2.2\" -DYYTEXT_POINTER=1 -DLILENDIAN=1 -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DNO_PWD_RESET=1 -DOPENSSL_NO_KRB5=1 -DLINUX=1 -DHAVE_LIBCRYPTO=1 -DHAVE_LIBSSL=1 -DLINUX_FRAMER=1   -I. -I.     -g -O2 -Wall  -c -o gui_interface.o `test -f '../../common/gui_interface.c' || echo './'`../../common/gui_interface.c
gcc  -g -O2 -Wall    -o xsup_get_state  xsup_get_state.o gui_interface.o  -lfl -liw -lm -lssl -lcrypto
make[3]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_get_state'
make[3]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli'
make[2]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli'
make[2]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools'
make[1]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools'
make[1]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2'

```
and make check:
```
nishoba@LinUbuntu:~/TMP/xsupplicant-1.2.2$ sudo make check
Making check in src
make[1]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/src'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/src'
Making check in etc
make[1]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/etc'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/etc'
Making check in tools
make[1]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/tools'
Making check in config-parser
make[2]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/tools/config-parser'
make[2]: Nothing to be done for `check'.
make[2]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/tools/config-parser'
make[2]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/tools'
make[2]: Nothing to be done for `check-am'.
make[2]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/tools'
make[1]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/tools'
Making check in doc
make[1]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/doc'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/doc'
Making check in drivers
make[1]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/drivers'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/drivers'
Making check in gui_tools
make[1]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools'
Making check in cli
make[2]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli'
Making check in xsup_set_pwd
make[3]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_set_pwd'
make[3]: Nothing to be done for `check'.
make[3]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_set_pwd'
Making check in xsup_monitor
make[3]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_monitor'
make[3]: Nothing to be done for `check'.
make[3]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_monitor'
Making check in xsup_get_state
make[3]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_get_state'
make[3]: Nothing to be done for `check'.
make[3]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_get_state'
make[3]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli'
make[3]: Nothing to be done for `check-am'.
make[3]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli'
make[2]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli'
make[2]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools'
make[2]: Nothing to be done for `check-am'.
make[2]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools'
make[1]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools'
make[1]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2'
make[1]: Nothing to be done for `check-am'.
make[1]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2'
nishoba@LinUbuntu:~/TMP/xsupplicant-1.2.2$
```

make install(i didnt think i would work but i did it anyway:
```
nishoba@LinUbuntu:~/TMP/xsupplicant-1.2.2$ sudo make install
Making install in src
make[1]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/src'
make[2]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/src'
test -z "/usr/local/sbin" || mkdir -p -- "/usr/local/sbin"
  /usr/bin/install -c 'xsupplicant' '/usr/local/sbin/xsupplicant'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/src'
make[1]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/src'
Making install in etc
make[1]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/etc'
make[2]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/etc'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/etc'
make[1]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/etc'
Making install in tools
make[1]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/tools'
Making install in config-parser
make[2]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/tools/config-parser'
make[3]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/tools/config-parser'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'config-parser' '/usr/local/bin/config-parser'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/tools/config-parser'
make[2]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/tools/config-parser'
make[2]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/tools'
make[3]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/tools'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/tools'
make[2]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/tools'
make[1]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/tools'
Making install in doc
make[1]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/doc'
make[2]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/doc'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/doc'
make[1]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/doc'
Making install in drivers
make[1]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/drivers'
make[2]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/drivers'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/drivers'
make[1]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/drivers'
Making install in gui_tools
make[1]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools'
Making install in cli
make[2]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli'
Making install in xsup_set_pwd
make[3]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_set_pwd'
make[4]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_set_pwd'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'xsup_set_pwd' '/usr/local/bin/xsup_set_pwd'
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_set_pwd'
make[3]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_set_pwd'
Making install in xsup_monitor
make[3]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_monitor'
make[4]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_monitor'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'xsup_monitor' '/usr/local/bin/xsup_monitor'
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_monitor'
make[3]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_monitor'
Making install in xsup_get_state
make[3]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_get_state'
make[4]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_get_state'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'xsup_get_state' '/usr/local/bin/xsup_get_state'
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_get_state'
make[3]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli/xsup_get_state'
make[3]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli'
make[4]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli'
make[3]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli'
make[2]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools/cli'
make[2]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools'
make[3]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools'
make[2]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools'
make[1]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2/gui_tools'
make[1]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2'
make[2]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.2'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2'
make[1]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.2'

```

the same thing is with xsupplicant 1.2.2 and 1.2.4
what to do? why wont it work?

---

### Post by nishoba on 2006-04-20
and now 1.2.3

i get the same result for ./configure
but make makes different result at least now i get errors :( 
```
nishoba@LinUbuntu:~/TMP/xsupplicant-1.2.3$ sudo make
cd . && /bin/sh /home/nishoba/TMP/xsupplicant-1.2.3/missing --run aclocal-1.9
/home/nishoba/TMP/xsupplicant-1.2.3/missing: line 46: aclocal-1.9: command not found
WARNING: `aclocal-1.9' is missing on your system.  You should only need it if
         you modified `acinclude.m4' or `configure.in'.  You might want
         to install the `Automake' and `Perl' packages.  Grab them from
         any GNU archive site.
 cd . && /bin/sh /home/nishoba/TMP/xsupplicant-1.2.3/missing --run automake-1.9 --foreign
/home/nishoba/TMP/xsupplicant-1.2.3/missing: line 46: automake-1.9: command not found
WARNING: `automake-1.9' is missing on your system.  You should only need it if
         you modified `Makefile.am', `acinclude.m4' or `configure.in'.
         You might want to install the `Automake' and `Perl' packages.
         Grab them from any GNU archive site.
cd . && /bin/sh /home/nishoba/TMP/xsupplicant-1.2.3/missing --run autoconf
/home/nishoba/TMP/xsupplicant-1.2.3/missing: line 46: autoconf: command not found
WARNING: `autoconf' is missing on your system.  You should only need it if
         you modified `configure.in'.  You might want to install the
         `Autoconf' and `GNU m4' packages.  Grab them from any GNU
         archive site.
/bin/sh ./config.status --recheck
running /bin/sh ./configure   --no-create --no-recursion
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ranlib... ranlib
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
checking for bison... bison -y
checking for flex... flex
checking for yywrap in -lfl... yes
checking lex output file root... lex.yy
checking whether yytext is a pointer... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking whether byte ordering is bigendian... no
checking user defined path to OpenSSL...
checking user defined path to OpenSSL libraries...
checking user defined path to OpenSSL headers...
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking Operating System... Linux
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking for linux/wireless.h... yes
checking for iwlib.h... yes
checking iwlib version... 3 params
checking for CRYPTO_new_ex_data in -lcrypto... yes
checking for SSL_library_init in -lssl... yes
checking openssl/ssl.h usability... yes
checking openssl/ssl.h presence... yes
checking for openssl/ssl.h... yes
checking openssl/err.h usability... yes
checking openssl/err.h presence... yes
checking for openssl/err.h... yes
checking for native frame interface... linux
checking for procfs support... okay
!! Not building MADWIFI WPA support !!
configure: creating ./config.status
 /bin/sh ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating tools/Makefile
config.status: creating doc/Makefile
config.status: creating etc/Makefile
config.status: creating drivers/Makefile
config.status: creating tools/config-parser/Makefile
config.status: creating tools/ntpwdhash/Makefile
config.status: creating gui_tools/Makefile
config.status: creating gui_tools/cli/Makefile
config.status: creating gui_tools/cli/xsup_set_pwd/Makefile
config.status: creating gui_tools/cli/xsup_monitor/Makefile
config.status: creating gui_tools/cli/xsup_get_state/Makefile
config.status: creating lib/Makefile
config.status: creating lib/libxsupgui/Makefile
config.status: creating lib/libxsupconfig/Makefile
config.status: creating lib/libxsupconfwrite/Makefile
config.status: creating lib/libxsupconfcheck/Makefile
config.status: executing depfiles commands
Making all in lib
make[1]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.3/lib'
Making all in libxsupgui
make[2]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.3/lib/libxsupgui'gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"xsupplicant\" -DVERSION=\"1.2.3\" -DYYTEXT_POINTER=1 -DSTDC_HEADERS=1 -DLILENDIAN=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DNO_PWD_RESET=1 -DOPENSSL_NO_KRB5=1 -DLINUX=1 -DHAVE_SYS_SOCKET_H=1 -DHAVE_LINUX_WIRELESS_H=1 -DHAVE_IWLIB_H=1 -DNEW_IWLIB=1 -DHAVE_LIBCRYPTO=1 -DHAVE_LIBSSL=1 -DLINUX_FRAMER=1  -I. -I. ../../src    -g -O2 -Wall  -c xsupgui.c
gcc: ../../src: linker input file unused because linking not done
rm -f libxsupgui.a
ar cru libxsupgui.a xsupgui.o
ranlib libxsupgui.a
make[2]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.3/lib/libxsupgui'
Making all in libxsupconfig
make[2]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.3/lib/libxsupconfig'
bison -y -d   config_grammar.y
if test -f y.tab.h; then \
  to=`echo "config_grammar_H" | sed \
                -e 'y/abcdefghijklmnopqrstuvwxyz/ABCDEFGHIJKLMNOPQRSTUVWXYZ/' \
                -e 's/[^ABCDEFGHIJKLMNOPQRSTUVWXYZ]/_/g'`; \
  sed -e "/^#/!b" -e "s/Y_TAB_H/$to/g" -e "s|y\.tab\.h|config_grammar.h|" \
            y.tab.h >config_grammar.ht; \
  rm -f y.tab.h; \
  if cmp -s config_grammar.ht config_grammar.h; then \
    rm -f config_grammar.ht ;\
  else \
    mv config_grammar.ht config_grammar.h; \
  fi; \
fi
if test -f y.output; then \
  mv y.output config_grammar.output; \
fi
sed '/^#/ s|y\.tab\.c|config_grammar.c|' y.tab.c >config_grammar.ct && mv config_grammar.ct config_grammar.c
rm -f y.tab.c
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"xsupplicant\" -DVERSION=\"1.2.3\" -DYYTEXT_POINTER=1 -DSTDC_HEADERS=1 -DLILENDIAN=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DNO_PWD_RESET=1 -DOPENSSL_NO_KRB5=1 -DLINUX=1 -DHAVE_SYS_SOCKET_H=1 -DHAVE_LINUX_WIRELESS_H=1 -DHAVE_IWLIB_H=1 -DNEW_IWLIB=1 -DHAVE_LIBCRYPTO=1 -DHAVE_LIBSSL=1 -DLINUX_FRAMER=1  -I. -I. -I ../../src    -g -O2 -Wall  -c config_grammar.c
flex   config_lexicon.l
sed '/^#/ s|lex.yy\.c|config_lexicon.c|' lex.yy.c >config_lexicon.c
rm -f lex.yy.c
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"xsupplicant\" -DVERSION=\"1.2.3\" -DYYTEXT_POINTER=1 -DSTDC_HEADERS=1 -DLILENDIAN=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DNO_PWD_RESET=1 -DOPENSSL_NO_KRB5=1 -DLINUX=1 -DHAVE_SYS_SOCKET_H=1 -DHAVE_LINUX_WIRELESS_H=1 -DHAVE_IWLIB_H=1 -DNEW_IWLIB=1 -DHAVE_LIBCRYPTO=1 -DHAVE_LIBSSL=1 -DLINUX_FRAMER=1  -I. -I. -I ../../src    -g -O2 -Wall  -c config_lexicon.c
config_lexicon.c:2234: warning: â€&#152;yyunputâ€™ defined but not used
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"xsupplicant\" -DVERSION=\"1.2.3\" -DYYTEXT_POINTER=1 -DSTDC_HEADERS=1 -DLILENDIAN=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DNO_PWD_RESET=1 -DOPENSSL_NO_KRB5=1 -DLINUX=1 -DHAVE_SYS_SOCKET_H=1 -DHAVE_LINUX_WIRELESS_H=1 -DHAVE_IWLIB_H=1 -DNEW_IWLIB=1 -DHAVE_LIBCRYPTO=1 -DHAVE_LIBSSL=1 -DLINUX_FRAMER=1  -I. -I. -I ../../src    -g -O2 -Wall  -c xsupconfig.c
rm -f libxsupconfig.a
ar cru libxsupconfig.a config_grammar.o config_lexicon.o xsupconfig.o
ranlib libxsupconfig.a
make[2]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.3/lib/libxsupconfig'
Making all in libxsupconfwrite
make[2]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.3/lib/libxsupconfwrite'
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"xsupplicant\" -DVERSION=\"1.2.3\" -DYYTEXT_POINTER=1 -DSTDC_HEADERS=1 -DLILENDIAN=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DNO_PWD_RESET=1 -DOPENSSL_NO_KRB5=1 -DLINUX=1 -DHAVE_SYS_SOCKET_H=1 -DHAVE_LINUX_WIRELESS_H=1 -DHAVE_IWLIB_H=1 -DNEW_IWLIB=1 -DHAVE_LIBCRYPTO=1 -DHAVE_LIBSSL=1 -DLINUX_FRAMER=1  -I. -I. -I ../../lib/libxsupconfig    -g -O2 -Wall  -c xsupconfwrite.c
xsupconfwrite.c: In function â€&#152;xsupconfwrite_networkâ€™:
xsupconfwrite.c:3571: warning: pointer targets in passing argument 1 of â€&#152;strlenâ€™ differ in signedness
xsupconfwrite.c:3571: warning: pointer targets in passing argument 1 of â€&#152;strlenâ€™ differ in signedness
xsupconfwrite.c:3571: warning: pointer targets in passing argument 1 of â€&#152;__builtin_strcmpâ€™ differ in signedness
xsupconfwrite.c:3571: warning: pointer targets in passing argument 1 of â€&#152;strlenâ€™ differ in signedness
xsupconfwrite.c:3571: warning: pointer targets in passing argument 1 of â€&#152;__builtin_strcmpâ€™ differ in signedness
xsupconfwrite.c:3571: warning: pointer targets in passing argument 1 of â€&#152;__builtin_strcmpâ€™ differ in signedness
xsupconfwrite.c:3571: warning: pointer targets in passing argument 1 of â€&#152;__builtin_strcmpâ€™ differ in signedness
xsupconfwrite.c:3571: warning: pointer targets in passing argument 1 of â€&#152;strncmpâ€™ differ in signedness
rm -f libxsupconfwrite.a
ar cru libxsupconfwrite.a xsupconfwrite.o
ranlib libxsupconfwrite.a
make[2]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.3/lib/libxsupconfwrite'
Making all in libxsupconfcheck
make[2]: Entering directory `/home/nishoba/TMP/xsupplicant-1.2.3/lib/libxsupconfcheck'
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"xsupplicant\" -DVERSION=\"1.2.3\" -DYYTEXT_POINTER=1 -DSTDC_HEADERS=1 -DLILENDIAN=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DNO_PWD_RESET=1 -DOPENSSL_NO_KRB5=1 -DLINUX=1 -DHAVE_SYS_SOCKET_H=1 -DHAVE_LINUX_WIRELESS_H=1 -DHAVE_IWLIB_H=1 -DNEW_IWLIB=1 -DHAVE_LIBCRYPTO=1 -DHAVE_LIBSSL=1 -DLINUX_FRAMER=1  -I. -I. -I ../../src    -g -O2 -Wall  -c xsupconfcheck.c
xsupconfcheck.c:7:24: error: xsupconfig.h: No such file or directory
In file included from xsupconfcheck.c:8:
xsupconfcheck.h:18: warning: â€&#152;struct config_dataâ€™ declared inside parameter listxsupconfcheck.h:18: warning: its scope is only this definition or declaration, which is probably not what you want
xsupconfcheck.h:19: warning: â€&#152;struct config_networkâ€™ declared inside parameter list
xsupconfcheck.h:21: warning: â€&#152;struct config_eap_methodâ€™ declared inside parameter list
xsupconfcheck.h:23: warning: â€&#152;struct config_static_wepâ€™ declared inside parameter list
xsupconfcheck.h:24: warning: â€&#152;struct config_wpa_pskâ€™ declared inside parameter list
xsupconfcheck.h:25: warning: â€&#152;struct config_eap_md5â€™ declared inside parameter list
xsupconfcheck.h:26: warning: â€&#152;struct config_eap_otpâ€™ declared inside parameter list
xsupconfcheck.h:27: warning: â€&#152;struct config_eap_otpâ€™ declared inside parameter list
xsupconfcheck.h:28: warning: â€&#152;struct config_eap_tlsâ€™ declared inside parameter list
xsupconfcheck.h:29: warning: â€&#152;struct config_eap_leapâ€™ declared inside parameter list
xsupconfcheck.h:31: warning: â€&#152;struct config_eap_mschapv2â€™ declared inside parameter list
xsupconfcheck.h:32: warning: â€&#152;struct config_eap_simâ€™ declared inside parameter list
xsupconfcheck.h:33: warning: â€&#152;struct config_eap_akaâ€™ declared inside parameter list
xsupconfcheck.h:34: warning: â€&#152;struct config_eap_peapâ€™ declared inside parameter list
xsupconfcheck.h:35: warning: â€&#152;struct config_eap_ttlsâ€™ declared inside parameter list
xsupconfcheck.c:67: warning: â€&#152;struct config_globalsâ€™ declared inside parameter list
xsupconfcheck.c: In function â€&#152;xsupconfcheck_check_globalsâ€™:
xsupconfcheck.c:72: error: dereferencing pointer to incomplete type
xsupconfcheck.c:78: error: dereferencing pointer to incomplete type
xsupconfcheck.c: At top level:
xsupconfcheck.c:93: warning: â€&#152;struct config_static_wepâ€™ declared inside parameter list
xsupconfcheck.c:94: error: conflicting types for â€&#152;xsupconfcheck_check_static_wep_methodâ€™
xsupconfcheck.h:23: error: previous declaration of â€&#152;xsupconfcheck_check_static_wep_methodâ€™ was here
xsupconfcheck.c: In function â€&#152;xsupconfcheck_check_static_wep_methodâ€™:
xsupconfcheck.c:98: error: dereferencing pointer to incomplete type
xsupconfcheck.c:98: error: dereferencing pointer to incomplete type
xsupconfcheck.c:106: error: dereferencing pointer to incomplete type
xsupconfcheck.c:106: error: dereferencing pointer to incomplete type
xsupconfcheck.c:115: error: dereferencing pointer to incomplete type
xsupconfcheck.c:115: error: dereferencing pointer to incomplete type
xsupconfcheck.c:122: error: dereferencing pointer to incomplete type
xsupconfcheck.c: At top level:
xsupconfcheck.c:137: warning: â€&#152;struct config_static_wepâ€™ declared inside parameter list
xsupconfcheck.c: In function â€&#152;xsupconfcheck_check_initial_wep_methodâ€™:
xsupconfcheck.c:142: error: dereferencing pointer to incomplete type
xsupconfcheck.c:142: error: dereferencing pointer to incomplete type
xsupconfcheck.c:150: error: dereferencing pointer to incomplete type
xsupconfcheck.c:150: error: dereferencing pointer to incomplete type
xsupconfcheck.c:159: error: dereferencing pointer to incomplete type
xsupconfcheck.c:159: error: dereferencing pointer to incomplete type
xsupconfcheck.c:166: error: dereferencing pointer to incomplete type
xsupconfcheck.c: At top level:
xsupconfcheck.c:181: warning: â€&#152;struct config_wpa_pskâ€™ declared inside parameter list
xsupconfcheck.c:182: error: conflicting types for â€&#152;xsupconfcheck_check_wpa_pskâ€™
xsupconfcheck.h:24: error: previous declaration of â€&#152;xsupconfcheck_check_wpa_pskâ€™ was here
xsupconfcheck.c: In function â€&#152;xsupconfcheck_check_wpa_pskâ€™:
xsupconfcheck.c:185: error: dereferencing pointer to incomplete type
xsupconfcheck.c:185: error: dereferencing pointer to incomplete type
xsupconfcheck.c: At top level:
xsupconfcheck.c:201: warning: â€&#152;struct config_eap_md5â€™ declared inside parameter list
xsupconfcheck.c:202: error: conflicting types for â€&#152;xsupconfcheck_check_eap_md5â€™
xsupconfcheck.h:25: error: previous declaration of â€&#152;xsupconfcheck_check_eap_md5â€™ was here
xsupconfcheck.c:218: warning: â€&#152;struct config_eap_otpâ€™ declared inside parameter list
xsupconfcheck.c:219: error: conflicting types for â€&#152;xsupconfcheck_check_eap_otpâ€™
xsupconfcheck.h:26: error: previous declaration of â€&#152;xsupconfcheck_check_eap_otpâ€™ was here
xsupconfcheck.c:235: warning: â€&#152;struct config_eap_otpâ€™ declared inside parameter list
xsupconfcheck.c:236: error: conflicting types for â€&#152;xsupconfcheck_check_eap_gtcâ€™
xsupconfcheck.h:27: error: previous declaration of â€&#152;xsupconfcheck_check_eap_gtcâ€™ was here
xsupconfcheck.c:253: warning: â€&#152;struct config_eap_tlsâ€™ declared inside parameter list
xsupconfcheck.c:254: error: conflicting types for â€&#152;xsupconfcheck_check_eap_tlsâ€™
xsupconfcheck.h:28: error: previous declaration of â€&#152;xsupconfcheck_check_eap_tlsâ€™ was here
xsupconfcheck.c: In function â€&#152;xsupconfcheck_check_eap_tlsâ€™:
xsupconfcheck.c:257: error: dereferencing pointer to incomplete type
xsupconfcheck.c:264: error: dereferencing pointer to incomplete type
xsupconfcheck.c:264: error: dereferencing pointer to incomplete type
xsupconfcheck.c:272: error: dereferencing pointer to incomplete type
xsupconfcheck.c: At top level:
xsupconfcheck.c:289: warning: â€&#152;struct config_eap_leapâ€™ declared inside parameter list
xsupconfcheck.c:290: error: conflicting types for â€&#152;xsupconfcheck_check_eap_leapâ€™xsupconfcheck.h:29: error: previous declaration of â€&#152;xsupconfcheck_check_eap_leapâ€™ was here
xsupconfcheck.c:306: warning: â€&#152;struct config_eap_mschapv2â€™ declared inside parameter list
xsupconfcheck.c:307: error: conflicting types for â€&#152;xsupconfcheck_check_eap_mschapv2â€™
xsupconfcheck.h:31: error: previous declaration of â€&#152;xsupconfcheck_check_eap_mschapv2â€™ was here
xsupconfcheck.c:323: warning: â€&#152;struct config_eap_simâ€™ declared inside parameter list
xsupconfcheck.c:324: error: conflicting types for â€&#152;xsupconfcheck_check_eap_simâ€™
xsupconfcheck.h:32: error: previous declaration of â€&#152;xsupconfcheck_check_eap_simâ€™ was here
xsupconfcheck.c:340: warning: â€&#152;struct config_eap_akaâ€™ declared inside parameter list
xsupconfcheck.c:341: error: conflicting types for â€&#152;xsupconfcheck_check_eap_akaâ€™
xsupconfcheck.h:33: error: previous declaration of â€&#152;xsupconfcheck_check_eap_akaâ€™ was here
xsupconfcheck.c:357: warning: â€&#152;struct config_eap_methodâ€™ declared inside parameter list
xsupconfcheck.c: In function â€&#152;xsupconfcheck_check_peap_phase2â€™:
xsupconfcheck.c:366: error: dereferencing pointer to incomplete type
xsupconfcheck.c:368: error: â€&#152;EAP_TYPE_MSCHAPV2â€™ undeclared (first use in this function)
xsupconfcheck.c:368: error: (Each undeclared identifier is reported only once
xsupconfcheck.c:368: error: for each function it appears in.)
xsupconfcheck.c:372: error: â€&#152;EAP_TYPE_MD5â€™ undeclared (first use in this function)
xsupconfcheck.c:376: error: â€&#152;EAP_TYPE_SIMâ€™ undeclared (first use in this function)
xsupconfcheck.c:380: error: â€&#152;EAP_TYPE_GTCâ€™ undeclared (first use in this function)
xsupconfcheck.c:384: error: â€&#152;EAP_TYPE_OTPâ€™ undeclared (first use in this function)
xsupconfcheck.c:395: error: dereferencing pointer to incomplete type
xsupconfcheck.c: At top level:
xsupconfcheck.c:408: warning: â€&#152;struct config_eap_peapâ€™ declared inside parameter list
xsupconfcheck.c:409: error: conflicting types for â€&#152;xsupconfcheck_check_eap_peapâ€™xsupconfcheck.h:34: error: previous declaration of â€&#152;xsupconfcheck_check_eap_peapâ€™ was here
xsupconfcheck.c: In function â€&#152;xsupconfcheck_check_eap_peapâ€™:
xsupconfcheck.c:412: error: dereferencing pointer to incomplete type
xsupconfcheck.c:412: error: dereferencing pointer to incomplete type
xsupconfcheck.c:420: error: dereferencing pointer to incomplete type
xsupconfcheck.c:427: error: dereferencing pointer to incomplete type
xsupconfcheck.c: At top level:
xsupconfcheck.c:439: warning: â€&#152;struct config_ttls_phase2â€™ declared inside parameter list
xsupconfcheck.c:457: warning: â€&#152;struct config_eap_ttlsâ€™ declared inside parameter list
xsupconfcheck.c:458: error: conflicting types for â€&#152;xsupconfcheck_check_eap_ttlsâ€™xsupconfcheck.h:35: error: previous declaration of â€&#152;xsupconfcheck_check_eap_ttlsâ€™ was here
xsupconfcheck.c: In function â€&#152;xsupconfcheck_check_eap_ttlsâ€™:
xsupconfcheck.c:461: error: dereferencing pointer to incomplete type
xsupconfcheck.c:461: error: dereferencing pointer to incomplete type
xsupconfcheck.c:469: error: dereferencing pointer to incomplete type
xsupconfcheck.c:469: error: â€&#152;TTLS_PHASE2_PAPâ€™ undeclared (first use in this function)
xsupconfcheck.c:469: error: dereferencing pointer to incomplete type
xsupconfcheck.c:469: error: â€&#152;TTLS_PHASE2_MSCHAPV2â€™ undeclared (first use in this function)
xsupconfcheck.c:477: error: dereferencing pointer to incomplete type
xsupconfcheck.c:483: error: dereferencing pointer to incomplete type
xsupconfcheck.c: At top level:
xsupconfcheck.c:497: warning: â€&#152;struct config_eap_methodâ€™ declared inside parameter list
xsupconfcheck.c:498: error: conflicting types for â€&#152;xsupconfcheck_check_eap_methodsâ€™
xsupconfcheck.h:21: error: previous declaration of â€&#152;xsupconfcheck_check_eap_methodsâ€™ was here
xsupconfcheck.c: In function â€&#152;xsupconfcheck_check_eap_methodsâ€™:
xsupconfcheck.c:506: error: dereferencing pointer to incomplete type
xsupconfcheck.c:508: error: â€&#152;STATIC_WEP_METHODâ€™ undeclared (first use in this function)
xsupconfcheck.c:509: error: dereferencing pointer to incomplete type
xsupconfcheck.c:513: error: â€&#152;WPA_PSKâ€™ undeclared (first use in this function)
xsupconfcheck.c:514: error: dereferencing pointer to incomplete type
xsupconfcheck.c:518: error: â€&#152;EAP_TYPE_MD5â€™ undeclared (first use in this function)
xsupconfcheck.c:519: error: dereferencing pointer to incomplete type
xsupconfcheck.c:523: error: â€&#152;EAP_TYPE_OTPâ€™ undeclared (first use in this function)
xsupconfcheck.c:524: error: dereferencing pointer to incomplete type
xsupconfcheck.c:528: error: â€&#152;EAP_TYPE_GTCâ€™ undeclared (first use in this function)
xsupconfcheck.c:529: error: dereferencing pointer to incomplete type
xsupconfcheck.c:533: error: â€&#152;EAP_TYPE_TLSâ€™ undeclared (first use in this function)
xsupconfcheck.c:534: error: dereferencing pointer to incomplete type
xsupconfcheck.c:538: error: â€&#152;EAP_TYPE_LEAPâ€™ undeclared (first use in this function)
xsupconfcheck.c:539: error: dereferencing pointer to incomplete type
xsupconfcheck.c:543: error: â€&#152;EAP_TYPE_SIMâ€™ undeclared (first use in this function)
xsupconfcheck.c:544: error: dereferencing pointer to incomplete type
xsupconfcheck.c:548: error: â€&#152;EAP_TYPE_TTLSâ€™ undeclared (first use in this function)
xsupconfcheck.c:549: error: dereferencing pointer to incomplete type
xsupconfcheck.c:553: error: â€&#152;EAP_TYPE_AKAâ€™ undeclared (first use in this function)
xsupconfcheck.c:554: error: dereferencing pointer to incomplete type
xsupconfcheck.c:558: error: â€&#152;EAP_TYPE_PEAPâ€™ undeclared (first use in this function)
xsupconfcheck.c:559: error: dereferencing pointer to incomplete type
xsupconfcheck.c:563: error: â€&#152;EAP_TYPE_MSCHAPV2â€™ undeclared (first use in this function)
xsupconfcheck.c:564: error: dereferencing pointer to incomplete type
xsupconfcheck.c:570: error: dereferencing pointer to incomplete type
xsupconfcheck.c: At top level:
xsupconfcheck.c:585: warning: â€&#152;struct config_networkâ€™ declared inside parameter list
xsupconfcheck.c:586: error: conflicting types for â€&#152;xsupconfcheck_check_networksâ€™xsupconfcheck.h:19: error: previous declaration of â€&#152;xsupconfcheck_check_networksâ€™ was here
xsupconfcheck.c: In function â€&#152;xsupconfcheck_check_networksâ€™:
xsupconfcheck.c:595: error: dereferencing pointer to incomplete type
xsupconfcheck.c:602: error: dereferencing pointer to incomplete type
xsupconfcheck.c:605: error: dereferencing pointer to incomplete type
xsupconfcheck.c:609: error: dereferencing pointer to incomplete type
xsupconfcheck.c:612: error: dereferencing pointer to incomplete type
xsupconfcheck.c:616: error: dereferencing pointer to incomplete type
xsupconfcheck.c:618: warning: implicit declaration of function â€&#152;xsupconfcheck_check_initial_wepâ€™
xsupconfcheck.c:618: error: dereferencing pointer to incomplete type
xsupconfcheck.c:618: error: dereferencing pointer to incomplete type
xsupconfcheck.c:622: error: dereferencing pointer to incomplete type
xsupconfcheck.c:622: error: dereferencing pointer to incomplete type
xsupconfcheck.c:626: error: dereferencing pointer to incomplete type
xsupconfcheck.c: At top level:
xsupconfcheck.c:638: warning: â€&#152;struct config_dataâ€™ declared inside parameter list
xsupconfcheck.c:639: error: conflicting types for â€&#152;xsupconfcheck_check_configâ€™
xsupconfcheck.h:18: error: previous declaration of â€&#152;xsupconfcheck_check_configâ€™ was here
xsupconfcheck.c: In function â€&#152;xsupconfcheck_check_configâ€™:
xsupconfcheck.c:642: error: dereferencing pointer to incomplete type
make[2]: *** [xsupconfcheck.o] Error 1
make[2]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.3/lib/libxsupconfcheck'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.3/lib'
make: *** [all-recursive] Error 1
```

???

---

### Post by croak77 on 2006-04-20
What's wrong with the first one? It seemed to make and make install fine. Did you use './configure --prefix=/usr'? Otherwise it installs to /usr/local so you might need the full path when running from terminal.

The second one you ran 'sudo make', its just 'make' after ./configure. And its says your're missing automake1.9. Make sure you have it installed

You should read through the docs, [http://sourceforge.net/docman/display_doc.php?docid=24379&group_id=60236](http://sourceforge.net/docman/display_doc.php?docid=24379&group_id=60236), maybe they will be some help to you.

---

### Post by nishoba on 2006-04-21
ok. it looks like it was ok the instalation before and xsupplicant worked fine(but not with my wireless network card(rt2500 pcmcia))
i think i need to make xsupplicant with madwifi support, so i do:
```
./configure --prefix=/USR/ --with-madwifi-path=/lib/modules/2.6.12-9-386/madwifi
```
and all is good until

```
nishoba@LinUbuntu:~/TMP/xsupplicant-1.2.4$make

...

-DENABLE_MADWIFI=1   -I. -I. -I /lib/modules/2.6.12-9-386/madwifi/ -I ../lib/libxsupconfig    -g -O2 -Wall  -c -o freebsd_core.o `test -f 'cardif/freebsd/freebsd_core.c' || echo './'`cardif/freebsd/freebsd_core.c
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"xsupplicant\" -DVERSION=\"1.2.4\" -DYYTEXT_POINTER=1 -DSTDC_HEADERS=1 -DLILENDIAN=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DNO_PWD_RESET=1 -DOPENSSL_NO_KRB5=1 -DLINUX=1 -DHAVE_SYS_SOCKET_H=1 -DHAVE_LINUX_WIRELESS_H=1 -DHAVE_IWLIB_H=1 -DNEW_IWLIB=1 -DHAVE_LIBCRYPTO=1 -DHAVE_LIBSSL=1 -DLINUX_FRAMER=1 -DENABLE_MADWIFI=1   -I. -I. -I /lib/modules/2.6.12-9-386/madwifi/ -I ../lib/libxsupconfig    -g -O2 -Wall  -c -o cardif_linux.o `test -f 'cardif/linux/cardif_linux.c' || echo './'`cardif/linux/cardif_linux.c
In file included from cardif/linux/cardif_linux.c:115:
/usr/include/linux/socket.h:7:2: warning: #warning "You should include <sys/socket.h>. This time I will do it for you."
cardif/linux/cardif_linux.c: In function â€&#152;cardif_setBSSIDâ€™:
cardif/linux/cardif_linux.c:1328: warning: pointer targets in passing argument 2 of â€&#152;wireless->setbssidâ€™ differ in signedness
cardif/linux/cardif_linux.c:1368:2: warning: #warning FINISH! We get scan data results, but we still need to do something with them.
cardif/linux/cardif_linux.c: In function â€&#152;cardif_passive_scan_timeoutâ€™:
cardif/linux/cardif_linux.c:1423: warning: pointer targets in assignment differ in signedness
cardif/linux/cardif_linux.c:1428: warning: pointer targets in passing argument 2 of â€&#152;debug_hex_printfâ€™ differ in signedness
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"xsupplicant\" -DVERSION=\"1.2.4\" -DYYTEXT_POINTER=1 -DSTDC_HEADERS=1 -DLILENDIAN=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DNO_PWD_RESET=1 -DOPENSSL_NO_KRB5=1 -DLINUX=1 -DHAVE_SYS_SOCKET_H=1 -DHAVE_LINUX_WIRELESS_H=1 -DHAVE_IWLIB_H=1 -DNEW_IWLIB=1 -DHAVE_LIBCRYPTO=1 -DHAVE_LIBSSL=1 -DLINUX_FRAMER=1 -DENABLE_MADWIFI=1   -I. -I. -I /lib/modules/2.6.12-9-386/madwifi/ -I ../lib/libxsupconfig    -g -O2 -Wall  -c -o linux_core.o `test -f 'cardif/linux/linux_core.c' || echo './'`cardif/linux/linux_core.c
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"xsupplicant\" -DVERSION=\"1.2.4\" -DYYTEXT_POINTER=1 -DSTDC_HEADERS=1 -DLILENDIAN=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DNO_PWD_RESET=1 -DOPENSSL_NO_KRB5=1 -DLINUX=1 -DHAVE_SYS_SOCKET_H=1 -DHAVE_LINUX_WIRELESS_H=1 -DHAVE_IWLIB_H=1 -DNEW_IWLIB=1 -DHAVE_LIBCRYPTO=1 -DHAVE_LIBSSL=1 -DLINUX_FRAMER=1 -DENABLE_MADWIFI=1   -I. -I. -I /lib/modules/2.6.12-9-386/madwifi/ -I ../lib/libxsupconfig    -g -O2 -Wall  -c -o cardif_linux_rtnetlink.o `test -f 'cardif/linux/cardif_linux_rtnetlink.c' || echo './'`cardif/linux/cardif_linux_rtnetlink.c
cardif/linux/cardif_linux_rtnetlink.c: In function â€&#152;cardif_linux_rtnetlink_parse_iesâ€™:
cardif/linux/cardif_linux_rtnetlink.c:637: warning: pointer targets in passing argument 1 of â€&#152;wpa_parse_ieâ€™ differ in signedness
cardif/linux/cardif_linux_rtnetlink.c:640: warning: pointer targets in assignment differ in signedness
cardif/linux/cardif_linux_rtnetlink.c:654: warning: pointer targets in passing argument 1 of â€&#152;wpa2_parse_ieâ€™ differ in signedness
cardif/linux/cardif_linux_rtnetlink.c:657: warning: pointer targets in assignment differ in signedness
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"xsupplicant\" -DVERSION=\"1.2.4\" -DYYTEXT_POINTER=1 -DSTDC_HEADERS=1 -DLILENDIAN=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DNO_PWD_RESET=1 -DOPENSSL_NO_KRB5=1 -DLINUX=1 -DHAVE_SYS_SOCKET_H=1 -DHAVE_LINUX_WIRELESS_H=1 -DHAVE_IWLIB_H=1 -DNEW_IWLIB=1 -DHAVE_LIBCRYPTO=1 -DHAVE_LIBSSL=1 -DLINUX_FRAMER=1 -DENABLE_MADWIFI=1   -I. -I. -I /lib/modules/2.6.12-9-386/madwifi/ -I ../lib/libxsupconfig    -g -O2 -Wall  -c -o cardif_atmel_driver.o `test -f 'cardif/linux/cardif_atmel_driver.c' || echo './'`cardif/linux/cardif_atmel_driver.c
In file included from cardif/linux/cardif_atmel_driver.c:78:
/usr/include/linux/socket.h:7:2: warning: #warning "You should include <sys/socket.h>. This time I will do it for you."
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"xsupplicant\" -DVERSION=\"1.2.4\" -DYYTEXT_POINTER=1 -DSTDC_HEADERS=1 -DLILENDIAN=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DNO_PWD_RESET=1 -DOPENSSL_NO_KRB5=1 -DLINUX=1 -DHAVE_SYS_SOCKET_H=1 -DHAVE_LINUX_WIRELESS_H=1 -DHAVE_IWLIB_H=1 -DNEW_IWLIB=1 -DHAVE_LIBCRYPTO=1 -DHAVE_LIBSSL=1 -DLINUX_FRAMER=1 -DENABLE_MADWIFI=1   -I. -I. -I /lib/modules/2.6.12-9-386/madwifi/ -I ../lib/libxsupconfig    -g -O2 -Wall  -c -o cardif_linux_wext.o `test -f 'cardif/linux/cardif_linux_wext.c' || echo './'`cardif/linux/cardif_linux_wext.c
In file included from cardif/linux/cardif_linux_wext.c:101:
/usr/include/linux/socket.h:7:2: warning: #warning "You should include <sys/socket.h>. This time I will do it for you."
cardif/linux/cardif_linux_wext.c: In function â€&#152;cardif_linux_wext_wep_associateâ€™:cardif/linux/cardif_linux_wext.c:796: warning: pointer targets in passing argument 2 of â€&#152;cardif_linux_wext_set_bssidâ€™ differ in signedness
cardif/linux/cardif_linux_wext.c: In function â€&#152;cardif_linux_wext_associateâ€™:
cardif/linux/cardif_linux_wext.c:1290: warning: pointer targets in passing argument 2 of â€&#152;cardif_linux_wext_set_bssidâ€™ differ in signedness
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"xsupplicant\" -DVERSION=\"1.2.4\" -DYYTEXT_POINTER=1 -DSTDC_HEADERS=1 -DLILENDIAN=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DNO_PWD_RESET=1 -DOPENSSL_NO_KRB5=1 -DLINUX=1 -DHAVE_SYS_SOCKET_H=1 -DHAVE_LINUX_WIRELESS_H=1 -DHAVE_IWLIB_H=1 -DNEW_IWLIB=1 -DHAVE_LIBCRYPTO=1 -DHAVE_LIBSSL=1 -DLINUX_FRAMER=1 -DENABLE_MADWIFI=1   -I. -I. -I /lib/modules/2.6.12-9-386/madwifi/ -I ../lib/libxsupconfig    -g -O2 -Wall  -c -o cardif_madwifi_driver.o `test -f 'cardif/linux/cardif_madwifi_driver.c' || echo './'`cardif/linux/cardif_madwifi_driver.c
In file included from cardif/linux/cardif_madwifi_driver.c:84:
/usr/include/linux/socket.h:7:2: warning: #warning "You should include <sys/socket.h>. This time I will do it for you."
cardif/linux/cardif_madwifi_driver.c:105:28: error: include/compat.h: No such file or directory
cardif/linux/cardif_madwifi_driver.c:106:33: error: net80211/_ieee80211.h: No such file or directory
cardif/linux/cardif_madwifi_driver.c:107:32: error: net80211/ieee80211.h: No such file or directory
cardif/linux/cardif_madwifi_driver.c:108:39: error: net80211/ieee80211_crypto.h: No such file or directory
cardif/linux/cardif_madwifi_driver.c:109:38: error: net80211/ieee80211_ioctl.h: No such file or directory
cardif/linux/cardif_madwifi_driver.c: In function â€&#152;set80211privâ€™:
cardif/linux/cardif_madwifi_driver.c:165: error: â€&#152;IEEE80211_IOCTL_SETPARAMâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c:165: error: (Each undeclared identifier is reported only once
cardif/linux/cardif_madwifi_driver.c:165: error: for each function it appears in.)
cardif/linux/cardif_madwifi_driver.c:166: error: â€&#152;IEEE80211_IOCTL_CHANLISTâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c: In function â€&#152;set80211paramâ€™:
cardif/linux/cardif_madwifi_driver.c:195: error: â€&#152;IEEE80211_IOCTL_SETPARAMâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c: In function â€&#152;cardif_madwifi_driver_get_wpa2_ieâ€™:
cardif/linux/cardif_madwifi_driver.c:217: warning: pointer targets in passing argument 2 of â€&#152;debug_hex_printfâ€™ differ in signedness
cardif/linux/cardif_madwifi_driver.c: In function â€&#152;cardif_madwifi_driver_set_wpa_ieâ€™:
cardif/linux/cardif_madwifi_driver.c:243: error: â€&#152;IEEE80211_IOCTL_SETOPTIEâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c: In function â€&#152;cardif_madwifi_driver_wpaâ€™:
cardif/linux/cardif_madwifi_driver.c:257: error: â€&#152;IEEE80211_PARAM_WPAâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c: In function â€&#152;cardif_madwifi_driver_wpa_stateâ€™:
cardif/linux/cardif_madwifi_driver.c:296: error: â€&#152;IEEE80211_PARAM_PRIVACYâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c:299: error: â€&#152;IEEE80211_PARAM_WPAâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c: In function â€&#152;cardif_madwifi_driver_del_keyâ€™:
cardif/linux/cardif_madwifi_driver.c:315: error: storage size of â€&#152;wkâ€™ isnâ€™t known
cardif/linux/cardif_madwifi_driver.c:321: error: â€&#152;IEEE80211_ADDR_LENâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c:323: error: â€&#152;IEEE80211_IOCTL_DELKEYâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c:315: warning: unused variable â€&#152;wkâ€™
cardif/linux/cardif_madwifi_driver.c: In function â€&#152;cardif_madwifi_driver_set_keyâ€™:
cardif/linux/cardif_madwifi_driver.c:330: error: storage size of â€&#152;wkâ€™ isnâ€™t known
cardif/linux/cardif_madwifi_driver.c:342: error: â€&#152;IEEE80211_CIPHER_WEPâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c:346: error: â€&#152;IEEE80211_CIPHER_TKIPâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c:350: error: â€&#152;IEEE80211_CIPHER_AES_CCMâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c:371: error: â€&#152;IEEE80211_KEY_RECVâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c:373: error: â€&#152;IEEE80211_KEY_XMITâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c:373: error: â€&#152;IEEE80211_KEY_DEFAULTâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c:374: error: â€&#152;IEEE80211_ADDR_LENâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c:381: warning: pointer targets in passing argument 2 of â€&#152;debug_hex_printfâ€™ differ in signedness
cardif/linux/cardif_madwifi_driver.c:384: warning: pointer targets in passing argument 2 of â€&#152;debug_hex_printfâ€™ differ in signedness
cardif/linux/cardif_madwifi_driver.c:386: error: â€&#152;IEEE80211_IOCTL_SETKEYâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c:330: warning: unused variable â€&#152;wkâ€™
cardif/linux/cardif_madwifi_driver.c: In function â€&#152;cardif_madwifi_driver_set_wepâ€™:
cardif/linux/cardif_madwifi_driver.c:409: warning: pointer targets in passing argument 3 of â€&#152;cardif_madwifi_driver_set_keyâ€™ differ in signedness
cardif/linux/cardif_madwifi_driver.c:409: warning: pointer targets in passing argument 8 of â€&#152;cardif_madwifi_driver_set_keyâ€™ differ in signedness
cardif/linux/cardif_madwifi_driver.c: In function â€&#152;cardif_madwifi_driver_disassociateâ€™:
cardif/linux/cardif_madwifi_driver.c:446: error: storage size of â€&#152;mlmeâ€™ isnâ€™t known
cardif/linux/cardif_madwifi_driver.c:448: error: â€&#152;IEEE80211_MLME_DISASSOCâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c:450: error: â€&#152;IEEE80211_ADDR_LENâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c:451: error: â€&#152;IEEE80211_IOCTL_SETMLMEâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c:446: warning: unused variable â€&#152;mlmeâ€™
cardif/linux/cardif_madwifi_driver.c: In function â€&#152;cardif_madwifi_driver_countermeasuresâ€™:
cardif/linux/cardif_madwifi_driver.c:458: error: â€&#152;IEEE80211_PARAM_COUNTERMEASURESâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c: In function â€&#152;cardif_madwifi_driver_drop_unencryptedâ€™:
cardif/linux/cardif_madwifi_driver.c:466: error: â€&#152;IEEE80211_PARAM_DROPUNENCRYPTEDâ€™ undeclared (first use in this function)
cardif/linux/cardif_madwifi_driver.c: In function â€&#152;cardif_madwifi_driver_roamâ€™:
cardif/linux/cardif_madwifi_driver.c:472: warning: implicit declaration of function â€&#152;cardif_madwifi_driver_associateâ€™
cardif/linux/cardif_madwifi_driver.c: At top level:
cardif/linux/cardif_madwifi_driver.c:477: warning: conflicting types for â€&#152;cardif_madwifi_driver_associateâ€™
cardif/linux/cardif_madwifi_driver.c:472: warning: previous implicit declaration of â€&#152;cardif_madwifi_driver_associateâ€™ was here
cardif/linux/cardif_madwifi_driver.c: In function â€&#152;cardif_madwifi_driver_associateâ€™:
cardif/linux/cardif_madwifi_driver.c:488: warning: pointer targets in passing argument 2 of â€&#152;cardif_madwifi_driver_get_wpa2_ieâ€™ differ in signedness
cardif/linux/cardif_madwifi_driver.c:491: warning: pointer targets in passing argument 2 of â€&#152;cardif_madwifi_driver_get_wpa_ieâ€™ differ in signedness
cardif/linux/cardif_madwifi_driver.c:494: warning: pointer targets in passing argument 2 of â€&#152;cardif_madwifi_driver_set_wpa_ieâ€™ differ in signedness
make[1]: *** [cardif_madwifi_driver.o] Error 1
make[1]: Leaving directory `/home/nishoba/TMP/xsupplicant-1.2.4/src'
make: *** [all-recursive] Error 1
nishoba@LinUbuntu:~/TMP/xsupplicant-1.2.4$
```

what to do?

---

### Post by nishoba on 2006-04-21
all god
wasnt problem in madwifi, now it works

the problem is i cant load pages or anything after a while
i load xsupplicant, his log:
```
No configuration information for network "(null)" found.  Using default.
Your card is currently set for wireless network "FERwlan".  Looking for a config.
Scanning for wireless networks ...
cardif_linux_wext_delete_key : Not supported by WE(17)!
cardif_linux_wext_delete_key : Not supported by WE(17)!
cardif_linux_wext_delete_key : Not supported by WE(17)!
cardif_linux_wext_delete_key : Not supported by WE(17)!
cardif_linux_wext_delete_key : Not supported by WE(17)!
Listed SSID is FERwlan
****WARNING**** Turning off certificate verification is a *VERY* bad idea!  You should not use this mode outside of basic testing, as it will compromise the security of your connection!
Successfully authenticated ra0
*WARNING* This AP uses the key generated during the authentication
process.  If reauthentication doesn't happen frequently enough your connection
may not be very secure!

```
then i load dhclient to get ip adress:
```
nishoba@LinUbuntu:~$ sudo dhclient ra0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ra0/00:10:a7:2c:bc:a7
Sending on   LPF/ra0/00:10:a7:2c:bc:a7
Sending on   Socket/fallback
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPACK from 161.53.76.253
bound to 161.53.76.62 -- renewal in 4591 seconds.
nishoba@LinUbuntu:~$ 

```
then i surf pages normaly but after a while i cant anymore, so i kill xsupplicant and then load it again, and it works again for some time(4-5min)

help

---

