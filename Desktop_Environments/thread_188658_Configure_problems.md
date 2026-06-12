---
title: "Configure problems"
date: 2006-06-04
forum: Desktop Environments
---

### Post by Kirbysuperstar on 2006-06-04
I'm trying to install the last.fm plugin for XMMS, and the readme says to run ./configure . I do so, and it tells me that I don't have a C compiler installed. I got GCC, and tried again, and it returned this:

```
garethchoake@tfcnix:~/Desktop/xmms-scrobbler-0.3.6$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

So, how would I go about installing it?

---

### Post by Fafnir on 2006-06-04
Sorry if you've done this already, but you might want to try installing the 'build-essential' package - it basically contains just about everything you could possibly need to compile stuff. I know you've got the compiler, but there's a lot of supporting libraries and stuff you need as well... :-(

Get it from Synaptic, or open an xterm and type:

```
sudo apt-get install build-essential
```

Then just try again with ./configure, make, make install.

Hope that helps!

---

### Post by Kirbysuperstar on 2006-06-04
```
The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
E: Broken packages

```

Aww.

---

### Post by aysiu on 2006-06-04
[QUOTE=Kirbysuperstar]```
The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
E: Broken packages

```

Aww.[/QUOTE] Sounds as if you have conflicting repositories.

Get a fresh list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then try again ```
sudo aptitude update
sudo aptitude install build-essential
```

---

