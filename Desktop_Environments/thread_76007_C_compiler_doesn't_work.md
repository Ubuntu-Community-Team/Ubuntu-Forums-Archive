---
title: "C compiler doesn't work"
date: 2005-10-14
forum: Desktop Environments
---

### Post by quiteNewbee on 2005-10-14
I get the following error when running ./configure on zinf mp3 player

sentinel@sentinel:~/Desktop/Downloads/zinf-2.2.5$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking whether make sets $(MAKE)... (cached) no
checking for gm4... no
checking for m4... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Whats wrong? I've tried to run it with sudo ./configure

---

### Post by GeneralZod on 2005-10-14
```

sudo apt-get install build-essential

```

And don't run ./configure with sudo, as you may get horrible permissions errors when you come to build! :)

Also, be prepared for having to track down and install plenty of dependencies - this is one of the drawbacks of compiling from source :(.

---

### Post by Ampersand on 2005-10-14
Have you installed the 'build-essential' package from apt, or just gcc?

---

### Post by quiteNewbee on 2005-10-14
aha.... thanks! this looks promising. I only installed gcc. about to install the whole deal now.

---

