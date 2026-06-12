---
title: "I can't install anything--gcc isn't found by ubuntu"
date: 2007-09-19
forum: Desktop Environments
---

### Post by corwinspyre on 2007-09-19
I tried to install something, and the following errors occur.  Basically, anything I try to ./configure fails out because it can't find gcc.
```
./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cl.exe... no

```

Details:
--I'm running x86 version of ubuntu 7.04.  

--build-essentials is installed.  

--My $PATH looks like:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

--"locate /usr/bin/*gcc* turns out: ```
/usr/bin/c89-gcc
/usr/bin/c99-gcc
/usr/bin/gcc
/usr/bin/gcc-4.1
/usr/bin/gccbug
/usr/bin/gccbug-4.1
/usr/bin/gccmakedep
/usr/bin/gcc-3.4
/usr/bin/gccbug-3.4
/usr/bin/gcc-3.4
/usr/bin/gcc-4.1
/usr/bin/gccbug
/usr/bin/gccbug-4.1
/usr/bin/gccbug-3.4
/usr/bin/gccbug-3.4
/usr/bin/gccbug-4.1
/usr/bin/gccmakedep
/usr/bin/i486-linux-gnu-gcc
/usr/bin/i486-linux-gnu-gcc-4.1
/usr/bin/i486-linux-gnu-gcc-3.4
/usr/bin/i486-linux-gnu-gcc-3.4
/usr/bin/i486-linux-gnu-gcc-4.1
/usr/bin/winegcc

```

thanks a bunch!

---

### Post by geraldm on 2007-09-19
You may have a link that is broken. Try to execute:
/usr/bin/gcc --version
If it does not return the version correctly, fix the link.
Also, after just installing, you may need to flush the cache.  Execute (as root) ldconfig
Also get that space out of your $PATH

Gerald

---

### Post by corwinspyre on 2007-09-19
Thank you very much. You were right; they were broken links.  For some reason they pointed to gcc-4.1.2, and I have gcc-4.1 in /usr/bin.

I also removed the space in $PATH.  It seems weird I'd have these errors when everything I installed was from the ubuntu repos and using apt

---

