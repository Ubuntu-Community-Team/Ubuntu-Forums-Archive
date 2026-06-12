---
title: "How do i install the plugins &quot;Throw&quot; and &quot;stackswitch&quot;?"
date: 2010-07-19
forum: Desktop Environments
---

### Post by TheSudoSumo on 2010-07-19
Anyone help me on this? i'm aware it requires the use of 'cmake', i've installed the required plugins, and all i get is "missing make file"...I git cloned the packages properly...what do i do now?

---

### Post by mc4man on 2010-07-19
for stackswitch on lucid installed 
compiz-fusion-bcop (0.8.2-0ubuntu2)
compiz-dev (1:0.8.4-0ubuntu15.1)
ran 
make and then make install, (no sudo
> doug@doug-laptop:~/Downloads/stackswitch-compiz-0.8$ make
convert   : stackswitch.xml.in -> build/stackswitch.xml
bcop'ing  : build/stackswitch.xml -> build/stackswitch_options.h
bcop'ing  : build/stackswitch.xml -> build/stackswitch_options.c
schema    : build/stackswitch.xml -> build/compiz-stackswitch.schema
compiling : stackswitch.c -> build/stackswitch.lo
compiling : build/stackswitch_options.c -> build/stackswitch_options.lo
linking   : build/libstackswitch.la
doug@doug-laptop:~/Downloads/stackswitch-compiz-0.8$ make install 
install   : /home/doug/.compiz/plugins/libstackswitch.so
install   : /home/doug/.compiz/metadata/stackswitch.xml
install   : build/compiz-stackswitch.schema

 available in ccsm

got source here - [http://cgit.compiz.org/compiz/plugins/stackswitch/commit/?h=compiz-0.8](http://cgit.compiz.org/compiz/plugins/stackswitch/commit/?h=compiz-0.8)

do you have a different link you could post? ( would think there was something a bit  newer

---

### Post by maccam94 on 2010-07-21
After I did a lot of investigating, I figured out the latest git version is designed for the heavily redesigned compiz 0.9 (ubuntu 10.04 uses 0.8.6). Here is a link to the latest working commit:
[http://gitweb.compiz.org/?p=compiz/plugins/stackswitch;a=snapshot;h=8444675649f44450f1ef6805bb1e15181677b03b;sf=tgz](http://gitweb.compiz.org/?p=compiz/plugins/stackswitch;a=snapshot;h=8444675649f44450f1ef6805bb1e15181677b03b;sf=tgz)

That should compile with make install.

---

### Post by perpetuus.flamma on 2011-11-29
> **maccam94 said:**
> After I did a lot of investigating, I figured out the latest git version is designed for the heavily redesigned compiz 0.9 (ubuntu 10.04 uses 0.8.6). Here is a link to the latest working commit:
[http://gitweb.compiz.org/?p=compiz/plugins/stackswitch;a=snapshot;h=8444675649f44450f1ef6805bb1e15181677b03b;sf=tgz](http://gitweb.compiz.org/?p=compiz/plugins/stackswitch;a=snapshot;h=8444675649f44450f1ef6805bb1e15181677b03b;sf=tgz)

That should compile with make install.

Why does mine show this on the terminal after executing a make install?

Makefile:58: *** [ERROR] No package 'compiz-text' found.  Stop.

---

