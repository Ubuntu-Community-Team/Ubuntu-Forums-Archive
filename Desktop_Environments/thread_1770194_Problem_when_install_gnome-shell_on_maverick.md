---
title: "Problem when install gnome-shell on maverick"
date: 2011-05-28
forum: Desktop Environments
---

### Post by yo_bhan on 2011-05-28
Hi guys,
I'm noob on ubuntu, I tried install gnome-shell from this link
[]("http://www.linuxlearningzone.com/install-gnome-shell-from-git-in-ubuntu-10-10-maverick-meerkat/")[http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html](http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html)

but i got an error 
like this
```

*** Error during phase build of evolution-data-server: ########## Error running make   *** [18/43]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 6
Type "yes" to confirm the action: yes
*** Checking out evolution-data-server *** [18/43]
rm -rf /home/didul/gnome-shell/source/evolution-data-server
git clone git://git.gnome.org/evolution-data-server
Cloning into evolution-data-server...
remote: Counting objects: 111719, done.
remote: Compressing objects: 100% (19168/19168), done.


```I choose 6, but I got an error like this again.
I repeat 5 times but still have same problem
```

Copying file m4/intl.m4
Copying file m4/intldir.m4
Copying file m4/intlmacosx.m4
Copying file m4/intmax.m4
Copying file m4/inttypes-pri.m4
Copying file m4/inttypes_h.m4
Copying file m4/lcmessage.m4
Copying file m4/lib-ld.m4
Copying file m4/lib-link.m4
Copying file m4/lib-prefix.m4
Copying file m4/lock.m4
Copying file m4/longlong.m4
Copying file m4/nls.m4
Copying file m4/po.m4
Copying file m4/printf-posix.m4
Copying file m4/progtest.m4
Copying file m4/size_max.m4
Copying file m4/stdint_h.m4
Copying file m4/uintmax_t.m4
Copying file m4/visibility.m4
Copying file m4/wchar_t.m4
Copying file m4/wint_t.m4
Copying file m4/xsize.m4
Copying file po/Makefile.in.in
Copying file po/Makevars.template
Copying file po/Rules-quot
Copying file po/boldquot.sed
Copying file po/en@boldquot.header
Copying file po/en@quot.header
Copying file po/insert-header.sin
Copying file po/quot.sed
Copying file po/remove-potcdate.sin
Running intltoolize...
Running gtkdocize...
Running aclocal-1.11...
configure.ac:22: warning: AC_INIT: not a literal: http://bugzilla.gnome.org/enter_bug.cgi?product=Evolution-Data-Server
Running autoconf...
configure.ac:22: warning: AC_INIT: not a literal: http://bugzilla.gnome.org/enter_bug.cgi?product=Evolution-Data-Server
Running autoheader...
configure.ac:22: warning: AC_INIT: not a literal: http://bugzilla.gnome.org/enter_bug.cgi?product=Evolution-Data-Server
Running automake-1.11...
configure.ac:22: warning: AC_INIT: not a literal: http://bugzilla.gnome.org/enter_bug.cgi?product=Evolution-Data-Server
configure.ac:205: installing `./compile'
configure.ac:246: installing `./config.guess'
configure.ac:246: installing `./config.sub'
configure.ac:23: installing `./install-sh'
configure.ac:23: installing `./missing'
addressbook/backends/file/Makefile.am: installing `./depcomp'
Running ./configure --enable-maintainer-mode --prefix /home/didul/gnome-shell/install --libdir /home/didul/gnome-shell/install/lib --disable-static --disable-gtk-doc ...
checking for a BSD-compatible install... /usr/bin/install-check
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for supported compiler flags...  -DG_DISABLE_DEPRECATED -DPANGO_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DG_DISABLE_SINGLE_INCLUDES -DGTK_DISABLE_SINGLE_INCLUDES -DGSEAL_ENABLE -Wall -Wextra -Wno-missing-field-initializers -Wno-sign-compare -Wno-unused-parameter -Wdeclaration-after-statement -Werror-implicit-function-declaration -Wformat-security -Winit-self -Wmissing-declarations -Wmissing-include-dirs -Wmissing-noreturn -Wnested-externs -Wpointer-arith -Wredundant-decls -Wundef -Wwrite-strings
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for inline... inline
checking whether gcc and cc understand -c and -o together... yes
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for flex... flex
checking lex output file root... lex.yy
checking lex library... -lfl
checking whether yytext is a pointer... yes
checking for bison... bison -y
checking for jw... no
checking whether NLS is requested... yes
checking for intltool >= 0.35.5... 0.41.1 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.1
checking for XML::Parser... ok
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... (cached) /usr/bin/msgmerge
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
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
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for gtkdoc-check... /usr/bin/gtkdoc-check
checking for gtkdoc-rebase... /usr/bin/gtkdoc-rebase
checking for gtkdoc-mkpdf... /usr/bin/gtkdoc-mkpdf
checking whether to build gtk-doc documentation... no
checking for Win32... no
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for fsync... yes
checking for strptime... yes
checking for strtok_r... yes
checking for nl_langinfo... yes
checking for GNOME_PLATFORM... yes
checking for GNOME_KEYRING... yes
checking for regexec... yes
checking Berkeley DB... yes
checking for iconv in -liconv... no
checking for iconv... yes
checking for gnu_get_libc_version... yes
checking if iconv() handles UTF-8... yes
checking preferred charset name formats for system iconv... found
checking for nl_langinfo (CODESET)... yes
checking for %l and %k support in strftime... yes
checking Mozilla NSPR pkg-config module name... nspr
checking Mozilla NSS pkg-config module name... nss
checking for sendmail... /usr/sbin/sendmail
checking system mail directory... /var/mail, writable by group mail
checking for tm_gmtoff in struct tm... yes
checking if ctime_r wants three arguments... no
checking for gethostbyname_r... yes
checking if gethostbyname_r wants five arguments... no
checking for gethostbyaddr_r... yes
checking if gethostbyaddr_r wants seven arguments... no
checking for sys/statvfs.h... yes
checking for statvfs... yes
checking for sys/param.h... yes
checking for sys/mount.h... yes
checking for statfs... yes
checking if system supports getaddrinfo and getnameinfo... yes
checking wspiapi.h usability... no
checking wspiapi.h presence... no
checking for wspiapi.h... no
checking if we should build the calendar... yes
checking if we should build the weather calendar backend... yes
checking for LIBGWEATHER... yes
checking for SunOS broken spool format... no
checking for Kerberos 5... no
checking for et/com_err.h... yes
checking for com_err.h... yes
checking for purify... impure
checking for OpenLDAP... no
checking for SunLDAP... no
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.0.0... yes (version 2.29.5)
checking for E_DATA_SERVER... yes
checking for E_DATA_SERVER_UI... yes
checking for E_BACKEND... yes
checking for EVOLUTION_ADDRESSBOOK... yes
checking for EVOLUTION_CALENDAR... yes
checking ical_set_unknown_token_handling_setting function... no
checking for GDATA... yes
checking for SOUP... yes
checking for deflateEnd in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGEFILE64_SOURCE value needed for large files... yes
checking for CAMEL... yes
checking for gconftool-2... /home/didul/gnome-shell/install/bin/gconftool-2
Using config source xml:merged:/home/didul/gnome-shell/install/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for gperf... /usr/bin/gperf
checking for gobject-introspection... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating evolution-data-server-zip
config.status: creating evolution-data-server.pc
config.status: creating addressbook/Makefile
config.status: creating addressbook/libebook/Makefile
config.status: creating addressbook/libebook/libebook.pc
config.status: creating addressbook/libedata-book/Makefile
config.status: creating addressbook/libedata-book/libedata-book.pc
config.status: creating addressbook/libegdbus/Makefile
config.status: creating addressbook/backends/Makefile
config.status: creating addressbook/backends/file/Makefile
config.status: creating addressbook/backends/vcf/Makefile
config.status: creating addressbook/backends/ldap/Makefile
config.status: creating addressbook/backends/google/Makefile
config.status: creating addressbook/backends/webdav/Makefile
config.status: creating art/Makefile
config.status: creating calendar/Makefile
config.status: creating calendar/libecal/Makefile
config.status: creating calendar/libecal/libecal.pc
config.status: creating calendar/libedata-cal/Makefile
config.status: creating calendar/libedata-cal/libedata-cal.pc
config.status: creating calendar/libegdbus/Makefile
config.status: creating calendar/backends/Makefile
config.status: creating calendar/backends/caldav/Makefile
config.status: creating calendar/backends/file/Makefile
config.status: creating calendar/backends/http/Makefile
config.status: creating calendar/backends/contacts/Makefile
config.status: creating calendar/backends/weather/Makefile
config.status: creating camel/Makefile
config.status: creating camel/providers/Makefile
config.status: creating camel/providers/imap/Makefile
config.status: creating camel/providers/imapx/Makefile
config.status: creating camel/providers/local/Makefile
config.status: creating camel/providers/nntp/Makefile
config.status: creating camel/providers/pop3/Makefile
config.status: creating camel/providers/sendmail/Makefile
config.status: creating camel/providers/smtp/Makefile
config.status: creating camel/tests/Makefile
config.status: creating camel/tests/folder/Makefile
config.status: creating camel/tests/lib/Makefile
config.status: creating camel/tests/message/Makefile
config.status: creating camel/tests/mime-filter/Makefile
config.status: creating camel/tests/misc/Makefile
config.status: creating camel/tests/smime/Makefile
config.status: creating camel/camel.pc
config.status: creating camel/camel-provider.pc
config.status: creating libebackend/Makefile
config.status: creating libebackend/libebackend.pc
config.status: creating libedataserver/Makefile
config.status: creating libedataserver/eds-version.h
config.status: creating libedataserver/libedataserver.pc
config.status: creating libedataserverui/Makefile
config.status: creating libedataserverui/libedataserverui.pc
config.status: creating tests/Makefile
config.status: creating tests/libebook/Makefile
config.status: creating tests/libebook/client/Makefile
config.status: creating tests/libebook/vcard/Makefile
config.status: creating tests/libecal/Makefile
config.status: creating tests/libecal/client/Makefile
config.status: creating tests/libedata-cal/Makefile
config.status: creating tests/libedataserver/Makefile
config.status: creating tests/libedataserverui/Makefile
config.status: creating docs/Makefile
config.status: creating docs/reference/Makefile
config.status: creating docs/reference/addressbook/Makefile
config.status: creating docs/reference/addressbook/libebook/Makefile
config.status: creating docs/reference/addressbook/libedata-book/Makefile
config.status: creating docs/reference/calendar/Makefile
config.status: creating docs/reference/calendar/libecal/Makefile
config.status: creating docs/reference/calendar/libedata-cal/Makefile
config.status: creating docs/reference/camel/Makefile
config.status: creating docs/reference/libedataserver/Makefile
config.status: creating docs/reference/libedataserverui/Makefile
config.status: creating docs/reference/libebackend/Makefile
config.status: creating po/Makefile.in
config.status: creating vala/Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing po-directories commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
config.status: executing libtool commands
config.status: executing po/stamp-it commands

    evolution-data-server has been configured as follows:
    Calendar:        yes
    Weather calendar:    yes
    Mail Directory:        /var/mail, writable by group mail
    LDAP support:        no
    NNTP support:        yes
    Kerberos 5:        no
    SSL support:        yes
    SMIME support:        yes
    IPv6 support:        yes
    Dot Locking:        yes
    File Locking:        fcntl
    Large files:        yes
    Gtk Doc:        no
    Introspection:        auto
    Vala bindings:        no

Now type `make' to compile evolution-data-server
*** Building evolution-data-server *** [18/43]
make  
  GEN    .gitignore
make[1]: Entering directory `/home/didul/gnome-shell/source/evolution-data-server'
make[2]: Entering directory `/home/didul/gnome-shell/source/evolution-data-server/vala'
  GEN    .gitignore
make[2]: Leaving directory `/home/didul/gnome-shell/source/evolution-data-server/vala'
make[1]: Leaving directory `/home/didul/gnome-shell/source/evolution-data-server'
make  all-recursive
make[1]: Entering directory `/home/didul/gnome-shell/source/evolution-data-server'
Making all in libedataserver
make[2]: Entering directory `/home/didul/gnome-shell/source/evolution-data-server/libedataserver'
( glib-genmarshal --prefix=e_gdbus_marshallers e-gdbus-marshallers.list --header > e-gdbus-marshallers.h.tmp \
    && mv e-gdbus-marshallers.h.tmp e-gdbus-marshallers.h ) || ( rm -f e-gdbus-marshallers.h.tmp && exit 1 )
( (echo "#include \"e-gdbus-marshallers.h\""; glib-genmarshal --prefix=e_gdbus_marshallers e-gdbus-marshallers.list --body) > e-gdbus-marshallers.c.tmp \
    && mv e-gdbus-marshallers.c.tmp e-gdbus-marshallers.c ) || ( rm -f e-gdbus-marshallers.c.tmp && exit 1 )
  GEN    .gitignore
make  all-am
make[3]: Entering directory `/home/didul/gnome-shell/source/evolution-data-server/libedataserver'
  CC     libedataserver_1_2_la-e-gdbus-marshallers.lo
  CC     libedataserver_1_2_la-e-account-list.lo
  CC     libedataserver_1_2_la-e-account.lo
  CC     libedataserver_1_2_la-e-categories.lo
  CC     libedataserver_1_2_la-e-client.lo
  CC     libedataserver_1_2_la-e-credentials.lo
  CC     libedataserver_1_2_la-e-flag.lo
  CC     libedataserver_1_2_la-e-gdbus-templates.lo
  CC     libedataserver_1_2_la-e-iterator.lo
  CC     libedataserver_1_2_la-e-list.lo
  CC     libedataserver_1_2_la-e-list-iterator.lo
  CC     libedataserver_1_2_la-e-memory.lo
  CC     libedataserver_1_2_la-e-operation-pool.lo
  CC     libedataserver_1_2_la-e-proxy.lo
  CC     libedataserver_1_2_la-e-sexp.lo
  CC     libedataserver_1_2_la-e-source-group.lo
  CC     libedataserver_1_2_la-e-source-list.lo
  CC     libedataserver_1_2_la-e-source.lo
  CC     libedataserver_1_2_la-e-debug-log.lo
  CC     libedataserver_1_2_la-e-time-utils.lo
  CC     libedataserver_1_2_la-e-uid.lo
  CC     libedataserver_1_2_la-e-url.lo
  CC     libedataserver_1_2_la-e-data-server-util.lo
  CC     libedataserver_1_2_la-e-xml-utils.lo
  CC     libedataserver_1_2_la-e-xml-hash-utils.lo
  CC     libedataserver_1_2_la-eds-version.lo
  CCLD   libedataserver-1.2.la
  GISCAN EDataServer-1.2.gir
/home/didul/gnome-shell/install/include/glib-2.0/glib/gthread.h:347: syntax error, unexpected '{' in '  if ((gpointer) (__extension__ ({ typedef struct { char Compile_Time_Assertion[(sizeof *(value_location) == sizeof (gpointer)) ? 1 : -1]; } _GStaticAssert_347; __sync_synchronize (); (gpointer) *(value_location); })) != ((void *)0))' at '{'
/home/didul/gnome-shell/install/include/glib-2.0/glib/gthread.h:347: syntax error, unexpected identifier in '  if ((gpointer) (__extension__ ({ typedef struct { char Compile_Time_Assertion[(sizeof *(value_location) == sizeof (gpointer)) ? 1 : -1]; } _GStaticAssert_347; __sync_synchronize (); (gpointer) *(value_location); })) != ((void *)0))' at '__sync_synchronize'
g-ir-scanner: EDataServer: warning: 208 warnings suppressed (use --warn-all to see them)
cp libedataserver.pc libedataserver-1.2.pc
  GICOMP EDataServer-1.2.gir
make[3]: Leaving directory `/home/didul/gnome-shell/source/evolution-data-server/libedataserver'
make[2]: Leaving directory `/home/didul/gnome-shell/source/evolution-data-server/libedataserver'
Making all in libebackend
make[2]: Entering directory `/home/didul/gnome-shell/source/evolution-data-server/libebackend'
  CC     libebackend_1_2_la-e-data-server-module.lo
  CC     libebackend_1_2_la-e-offline-listener.lo
  CC     libebackend_1_2_la-e-dbhash.lo
  CC     libebackend_1_2_la-e-db3-utils.lo
  CC     libebackend_1_2_la-e-file-cache.lo
  CCLD   libebackend-1.2.la
cp libebackend.pc libebackend-1.2.pc
  GEN    .gitignore
make[2]: Leaving directory `/home/didul/gnome-shell/source/evolution-data-server/libebackend'
Making all in camel
make[2]: Entering directory `/home/didul/gnome-shell/source/evolution-data-server/camel'
perl ./gentables.pl > camel-mime-tables.c
( glib-genmarshal --prefix=camel_marshal camel-marshal.list --header > camel-marshal.h.tmp \
    && mv camel-marshal.h.tmp camel-marshal.h ) || ( rm -f camel-marshal.h.tmp && exit 1 )
( (echo "#include \"camel-marshal.h\""; glib-genmarshal --prefix=camel_marshal camel-marshal.list --body) > camel-marshal.c.tmp \
    && mv camel-marshal.c.tmp camel-marshal.c ) || ( rm -f camel-marshal.c.tmp && exit 1 )
  GEN    .gitignore
make  all-recursive
make[3]: Entering directory `/home/didul/gnome-shell/source/evolution-data-server/camel'
Making all in .
make[4]: Entering directory `/home/didul/gnome-shell/source/evolution-data-server/camel'
  CC     libcamel_1_2_la-camel-marshal.lo
  CC     libcamel_1_2_la-camel-address.lo
  CC     libcamel_1_2_la-camel-block-file.lo
  CC     libcamel_1_2_la-camel-certdb.lo
  CC     libcamel_1_2_la-camel-charset-map.lo
  CC     libcamel_1_2_la-camel-data-cache.lo
  CC     libcamel_1_2_la-camel-data-wrapper.lo
  CC     libcamel_1_2_la-camel-db.lo
  CC     libcamel_1_2_la-camel-debug.lo
  CC     libcamel_1_2_la-camel-file-utils.lo
  CC     libcamel_1_2_la-camel-html-parser.lo
  CC     libcamel_1_2_la-camel-iconv.lo
  CC     libcamel_1_2_la-camel-index.lo
  CC     libcamel_1_2_la-camel-internet-address.lo
  CC     libcamel_1_2_la-camel-junk-plugin.lo
  CC     libcamel_1_2_la-camel-list-utils.lo
  CC     libcamel_1_2_la-camel-lock.lo
camel-lock.c: In function &#8216;camel_lock_dot&#8217;:
camel-lock.c:109: warning: ignoring return value of &#8216;link&#8217;, declared with attribute warn_unused_result
  CC     libcamel_1_2_la-camel-medium.lo
  CC     libcamel_1_2_la-camel-mempool.lo
  CC     libcamel_1_2_la-camel-mime-filter-basic.lo
  CC     libcamel_1_2_la-camel-mime-filter-bestenc.lo
  CC     libcamel_1_2_la-camel-mime-filter-canon.lo
  CC     libcamel_1_2_la-camel-mime-filter-charset.lo
  CC     libcamel_1_2_la-camel-mime-filter-crlf.lo
  CC     libcamel_1_2_la-camel-mime-filter-enriched.lo
  CC     libcamel_1_2_la-camel-mime-filter-from.lo
  CC     libcamel_1_2_la-camel-mime-filter-gzip.lo
  CC     libcamel_1_2_la-camel-mime-filter-html.lo
  CC     libcamel_1_2_la-camel-mime-filter-index.lo
  CC     libcamel_1_2_la-camel-mime-filter-linewrap.lo
  CC     libcamel_1_2_la-camel-mime-filter-pgp.lo
  CC     libcamel_1_2_la-camel-mime-filter-progress.lo
  CC     libcamel_1_2_la-camel-mime-filter-save.lo
  CC     libcamel_1_2_la-camel-mime-filter-tohtml.lo
  CC     libcamel_1_2_la-camel-mime-filter-windows.lo
  CC     libcamel_1_2_la-camel-mime-filter-yenc.lo
  CC     libcamel_1_2_la-camel-mime-filter.lo
  CC     libcamel_1_2_la-camel-mime-message.lo
  CC     libcamel_1_2_la-camel-mime-parser.lo
  CC     libcamel_1_2_la-camel-mime-part-utils.lo
  CC     libcamel_1_2_la-camel-mime-part.lo
  CC     libcamel_1_2_la-camel-mime-utils.lo
  CC     libcamel_1_2_la-camel-mime-tables.lo
  CC     libcamel_1_2_la-camel-msgport.lo
  CC     libcamel_1_2_la-camel-multipart-encrypted.lo
  CC     libcamel_1_2_la-camel-multipart-signed.lo
  CC     libcamel_1_2_la-camel-multipart.lo
  CC     libcamel_1_2_la-camel-net-utils.lo
  CC     libcamel_1_2_la-camel-nntp-address.lo
  CC     libcamel_1_2_la-camel-object.lo
  CC     libcamel_1_2_la-camel-object-bag.lo
  CC     libcamel_1_2_la-camel-operation.lo
camel-operation.c: In function &#8216;status_node_unref&#8217;:
camel-operation.c:101: error: implicit declaration of function &#8216;g_atomic_int_exchange_and_add&#8217;
camel-operation.c:101: warning: nested extern declaration of &#8216;g_atomic_int_exchange_and_add&#8217;
make[4]: *** [libcamel_1_2_la-camel-operation.lo] Error 1
make[4]: Leaving directory `/home/didul/gnome-shell/source/evolution-data-server/camel'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/didul/gnome-shell/source/evolution-data-server/camel'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/didul/gnome-shell/source/evolution-data-server/camel'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/didul/gnome-shell/source/evolution-data-server'
make: *** [all] Error 2
*** Error during phase build of evolution-data-server: ########## Error running make   *** [18/43]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 


```I tried searching on google cant find solution
could someone help me pliss :confused:

===============
edit 
problem solved

need install 
> sudo apt-get install  evolution-data-server-dev

sorry for my bad english
thanks for your response

---

