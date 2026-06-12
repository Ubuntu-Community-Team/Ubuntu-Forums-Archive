---
title: "Intrepid Ibex, Evolution &amp; Mail Notification"
date: 2009-06-29
forum: Desktop Environments
---

### Post by jolly.roger on 2009-06-29
Hey.

Having mail notification is such a cool gadget. You can be in a kitchen preparing lovely meal or out in the garden enjoying sun hot sun and cold pint and then you hear it. This demanding sound proclaiming to the world that YOU have new email. Full of excitement and hope, you run to you computer and... yap, spam....

So as all of you can see mail notification is essential to my happiness. And it happened so that last four hours i spend on (need i say that?) futile attempts of installing one. By no means I'm Linux guru, in fact I'm just starting to explore this new playground, and now it's time to ask for yours help. Listen to my story....

I'm running Intrepid Ibex and for my mail notification I did choose [Mail Notification]("http://www.nongnu.org/mailnotify/") by Jean-Yves Lefort, latest (5.4) version. First problems started durning compiling attenpt(s) - I was missing lots of packages. Among others: dbus-glib, dbus, expat, libglade, libnotify.... and probably few more which eludes me now. Time to try and compile Mail Notification again, and after running

this is what i get:

```
checking for ngettext(), dgettext(), bind_textdomain_codeset() in libc... yes
checking for msgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... yes
checking for gconftool-2... /usr/bin/gconftool-2
checking for scrollkeeper-preinstall... /usr/bin/scrollkeeper-preinstall
checking for scrollkeeper-update... /usr/bin/scrollkeeper-update
checking for scrollkeeper-config... /usr/bin/scrollkeeper-config
checking for the OMF directory... /usr/share/omf
checking for the ScrollKeeper database directory... /var/lib/rarian
checking for dbus-binding-tool... /usr/local/bin/dbus-binding-tool
checking for gob2... not found
checking the C compiler dependency style... GCC
checking for the GNU C library... yes
checking for pkg-config... /usr/bin/pkg-config
checking for GNOME... yes
checking for D-Bus... yes
checking for GMime... no
WARNING: Package gmime-2.0 was not found in the pkg-config search path.
WARNING: Perhaps you should add the directory containing `gmime-2.0.pc'
WARNING: to the PKG_CONFIG_PATH environment variable
WARNING: No package 'gmime-2.0' found
WARNING: disabling option "hotmail" since GMime was not found
WARNING: disabling option "imap" since GMime was not found
WARNING: disabling option "maildir" since GMime was not found
WARNING: disabling option "mbox" since GMime was not found
WARNING: disabling option "mh" since GMime was not found
WARNING: disabling option "mozilla" since GMime was not found
WARNING: disabling option "pop3" since GMime was not found
WARNING: disabling option "sylpheed" since GMime was not found
WARNING: disabling option "yahoo" since GMime was not found
checking for GNOME Keyring... yes
WARNING: disabling option "ipv6" since options "pop3" and "imap" are disabled
WARNING: disabling option "sasl" since options "pop3" and "imap" are disabled
WARNING: disabling option "ssl" since options "pop3" and "imap" are disabled
checking for Evolution... no
WARNING: Package evolution-plugin was not found in the pkg-config search path.
WARNING: Perhaps you should add the directory containing `evolution-plugin.pc'
WARNING: to the PKG_CONFIG_PATH environment variable
WARNING: No package 'evolution-plugin' found
WARNING: disabling option "evolution" since Evolution was not found
checking for timegm() in libc... yes

Mail Notification 5.4 was configured successfully.
The following variables are in effect:

  Compiler options:

    cc:                      cc
    cflags:                  -O2
    cppflags:                
    ldflags:                 
    libs:                    
    cc-dependency-tracking:  yes

  Installation options:

    destdir:                 
    prefix:                  /usr
    bindir:                  $prefix/bin
    libdir:                  $prefix/lib
    libexecdir:              $prefix/libexec
    datadir:                 $prefix/share
    sysconfdir:              $prefix/etc
    localstatedir:           $prefix/var
    data-mode:               0644
    data-owner:              
    data-group:              
    program-mode:            0755
    program-owner:           
    program-group:           
    library-mode:            0644
    library-owner:           
    library-group:           
    gconf-config-source:     xml:merged:/etc/gconf/gconf.xml.defaults
    gconf-schemas-dir:       $datadir/gconf/schemas
    install-gconf-schemas:   yes
    help-dir:                $datadir/gnome/help
    omf-dir:                 /usr/share/omf
    scrollkeeper-dir:        /var/lib/rarian
    evolution-plugin-dir:    autodetect

  External programs:

    msgfmt:                  /usr/bin/msgfmt
    perl:                    /usr/bin/perl
    gconftool-2:             /usr/bin/gconftool-2
    scrollkeeper-preinstall: /usr/bin/scrollkeeper-preinstall
    scrollkeeper-update:     /usr/bin/scrollkeeper-update
    dbus-binding-tool:       /usr/local/bin/dbus-binding-tool
    gob2:                    

  Mailbox backends:

    evolution:               no
    gmail:                   yes
    hotmail:                 no
    imap:                    no
    maildir:                 no
    mbox:                    no
    mh:                      no
    mozilla:                 no
    pop3:                    no
    sylpheed:                no
    yahoo:                   no

  IMAP and POP3 features:

    ipv6:                    no
    sasl:                    no
    ssl:                     no

```

So i don't have *GMime* and *evolution-plugins*. I will use Synaptic Packages Manager to check *evolution-plugins*... and i DO have it there and it's listed as INSTALLED already. Well, there is no harm in reinstalling it! Now back again to Mail Notification....

And i got exaclly same output. Reinstalling of *evolution-plugins* didn't help. Let's leave this for a moment and try with GMime...

./configure give us this output {for version 2.4.7):

```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking if building for Win32... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for inline... inline
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for rm... /bin/rm
checking for mv... /bin/mv
checking for tar... /bin/tar
checking for a sed that does not truncate output... /bin/sed
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
checking if gcc supports -c -o file.o... /bin/rm: cannot remove `conftest*': No such file or directory
yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... /bin/rm: cannot remove `conftest*': No such file or directory
no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for bash... /bin/bash
checking if dolt supports this host... yes, replacing libtool
checking whether to enable maintainer-specific portions of Makefiles... no
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking winsock2.h usability... no
checking winsock2.h presence... no
checking for winsock2.h... no
checking for string.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking poll.h usability... yes
checking poll.h presence... yes
checking for poll.h... yes
checking for off_t... yes
checking for size_t... yes
checking for ssize_t... yes
checking for nfds_t... yes
checking for strftime... yes
checking for localtime... yes
checking for gmtime_r... yes
checking for gmtime_s... no
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for munmap... yes
checking for msync... yes
checking for select... yes
checking for poll... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether to build gtk-doc documentation... no
checking for gtkdoc-check... no
checking for db2html... false
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.12.0... yes (version 2.20.1)
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for inflate in -lz... yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking preferred charset formats for system iconv... found
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for GNU getopt_long... yes
checking for fsync... yes
checking for MAXHOSTNAMELEN... yes
checking for domainname in struct utsname... yes
checking for tm_gmtoff in struct tm... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGEFILE64_SOURCE value needed for large files... yes
checking size of ssize_t... 4
checking size of size_t... 4
checking size of off_t... 8
checking for gethostname... yes
checking for getdomainname... yes
checking for getaddrinfo... yes
checking for getaddrinfo in -lsocket... no
checking for getaddrinfo in -lnsl... yes
checking for mcs... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating build/Makefile
config.status: creating build/vs2008/Makefile
config.status: creating docs/Makefile
config.status: creating docs/reference/Makefile
config.status: creating docs/tutorial/Makefile
config.status: creating examples/Makefile
config.status: creating util/Makefile
config.status: creating gmime/Makefile
config.status: creating mono/Makefile
config.status: creating mono/AssemblyInfo.cs
config.status: creating mono/gmime-sharp.dll.config
config.status: creating mono/gmime-sharp-2.4.pc
config.status: creating src/Makefile
config.status: creating tests/Makefile
config.status: creating tools/Makefile
config.status: creating gmime-2.4.pc
config.status: creating gmime.spec
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
/bin/rm: cannot remove `libtoolT': No such file or directory


Configuration:

  Source code location: /home/jollyroger/Downloads/gmime-2.4.7
  Install prefix:       /usr/local
  Compiler:             gcc

  Profiling enabled:    no

  Large file support:   yes
  Console warnings:     no

  Mono bindings:        no

```

Looks OK, so make......

```

make[3]: *** [test-mime.o] Error 1
make[3]: Leaving directory `/home/jollyroger/Desktop/mail/tests'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jollyroger/Desktop/mail/tests'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jollyroger/Desktop/mail'
make: *** [all] Error 2

```

I give up. At least for tonight - in 2.5h I have to get up and go to work... Any sugestions, ideas and explanations are more than welcome!

Help anyone?

-jolly roger

---

### Post by aged hippy on 2009-06-30
I've used Thunderbird for years, it fetches your mail for you without any fuss. :)

It's in the repositories. :popcorn:

---

### Post by jolly.roger on 2009-06-30
> 
I've used Thunderbird for years, it fetches your mail for you without any fuss.
Ha! It's Mail Notification which I'm more interested in. Thunderbird, Evolution, what ever. But I finally manage to get it work, sort of. Reason for Mail Notification not finding GMime and Evolution was simple - lack of packages. I mean, i did have both of them already but not *-dev.* So after upgrading my system with *libgmime-2*.2.21-1, *evolution-dev* there was no problem with compiling Mail Notification! Add *libssl-dev *and *libsasl2-dev* and done! Fully functional Mail Notification!

And here i realised that it's exactly the same Mail Notification which I could get from *Add/Remove...* Please, no comments.

But my problems didn't stop here. When I'm trying to add (in Mail Notification) new mailbox, choosing as a type Evolution, problems start. I have to have Evolution open to use it mailbox. Without it I'm getting:
 

>  
 Mail Notification can not contact Evolution. Make sure that Evolution is running and that the Evolution Jean-Yves Lefort's Mail Notification plugin is loaded.
 
 And when I try to open Evolution it starts and automatically shut itself down. In Mail Notification Mailbox List I got evolution-type mailbox, and comment under it says:
 

 > 
unhandled Evolution mailbox (unable to contact Evolution)
 
 So I got two questions:
 *primo. *Why it's happens?
 *Secundo.* What I can do to solve it?
 

 

 Jolly Roger

---

### Post by frogotronic on 2009-07-13
> **jolly.roger said:**
> Ha! It's Mail Notification which I'm more interested in. Thunderbird, Evolution, what ever. But I finally manage to get it work, sort of. Reason for Mail Notification not finding GMime and Evolution was simple - lack of packages. I mean, i did have both of them already but not *-dev.* So after upgrading my system with *libgmime-2*.2.21-1, *evolution-dev* there was no problem with compiling Mail Notification! Add *libssl-dev *and *libsasl2-dev* and done! Fully functional Mail Notification!

And here i realised that it's exactly the same Mail Notification which I could get from *Add/Remove...* Please, no comments.

But my problems didn't stop here. When I'm trying to add (in Mail Notification) new mailbox, choosing as a type Evolution, problems start. I have to have Evolution open to use it mailbox. Without it I'm getting:
 


 And when I try to open Evolution it starts and automatically shut itself down. In Mail Notification Mailbox List I got evolution-type mailbox, and comment under it says:
 

 
 So I got two questions:
 *primo. *Why it's happens?
 *Secundo.* What I can do to solve it?
 

 

 Jolly Roger

same problem here...

---

### Post by frogotronic on 2009-07-13
Try this:

[https://bugs.launchpad.net/ubuntu/+source/mail-notification/+bug/251031](https://bugs.launchpad.net/ubuntu/+source/mail-notification/+bug/251031) 

There are debs/repos listed halfway down

-CH

---

