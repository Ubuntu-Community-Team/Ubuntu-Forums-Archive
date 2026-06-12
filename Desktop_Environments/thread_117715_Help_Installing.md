---
title: "Help Installing"
date: 2006-01-15
forum: Desktop Environments
---

### Post by taikyo on 2006-01-15
For some reason I can't install this mmc mud client, everytime I use ./configure it gives me this error

> checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for mawk... mawk
checking whether make sets ${MAKE}... no
checking for perl... perl
checking C compiler... cc
checking C compiler flags...  -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I/usr/lib/perl/5.8/CORE  -O2
checking linker... cc
checking linker flags... -Wl,-E  -L/usr/local/lib /usr/lib/perl/5.8/auto/DynaLoader/DynaLoader.a -L/usr/lib/perl/5.8/CORE -lperl -ldl -lm -lpthread -lc -lcrypt
checking for gcc... cc
checking for C compiler default output... configure: error: C compiler cannot create executables


And I try using make but it says the make file isn't there.

Thanks for any help

---

### Post by taikyo on 2006-01-15
Okay, wierd it changed to:
```
norman@norman:~/Desktop/mmc$ ./configure
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking for perl... perl
checking C compiler... cc
checking C compiler flags...  -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I/usr/lib/perl/5.8/CORE  -O2
checking linker... cc
checking linker flags... -Wl,-E  -L/usr/local/lib /usr/lib/perl/5.8/auto/DynaLoader/DynaLoader.a -L/usr/lib/perl/5.8/CORE -lperl -ldl -lm -lpthread -lc -lcrypt
checking for gcc... cc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for executable suffix...
checking for object suffix... o
checking whether we are using the GNU C compiler... yes
checking whether cc accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of cc... none
checking module dependencies... Ex.pm CL.pm RStream.pm Conf.pm LE.pm Parser.pm MUD.pm Keymap.pm DCommand.pm CMD.pm UAPI.pm Status.pm Ticker.pm Main.pm
checking modules... Ex.pm CL.pm RStream.pm Conf.pm LE.pm Parser.pm MUD.pm Keymap.pm DCommand.pm CMD.pm UAPI.pm Status.pm Ticker.pm Main.pm
checking system modules... strict.pm integer.pm locale.pm Exporter.pm Carp.pm warnings.pm warnings/register.pm vars.pm fields.pm Symbol.pm base.pm  Carp::Heavy Exporter::Heavy
checking perl library dir... /usr/share/perl/5.8
checking for setupterm in -lncurses... no
checking for setupterm in -lcurses... no
configure: error: curses not found

```

Help please :)

---

