---
title: "Difficulty installing vDrift"
date: 2005-08-18
forum: Gaming &amp; Leisure
---

### Post by tofu1 on 2005-08-18
Hey,
I'm a complete linux n00b so please take it easy on me =)

I downloaded vdrift and decompressed it. I'm trying to follow the instructions but ./configure gives me this:

```
kevin@wind:~/Desktop/vdrift-2005-08-02$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

```

I checked the site and it tells me that i should ./autogen.sh
That gives me this:

```
kevin@wind:~/Desktop/vdrift-2005-08-02$ ./autogen
bash: ./autogen: No such file or directory
kevin@wind:~/Desktop/vdrift-2005-08-02$ ./autogen.sh
bash: ./autogen.sh: No such file or directory

```

Can anyone help me? I'm lost, and I really wanna play :)

//edit: NVM I realised I didn't have the proper libraries installed. Got it to work haha.

---

### Post by charlieg on 2005-08-18
You need to install gcc to compile things.  Then you'll also need a slew of -dev packages (e.g. libsdl-dev) which VDrift will require you to compile against.

To cut a long story short, wait a while because they'll release an autopackage of the next version, meaning you'll be able to install it rather than have to compile it.

---

