---
title: "Problem installing from source"
date: 2005-07-15
forum: Desktop Environments
---

### Post by master of all on 2005-07-15
Whenever I try to install anything from the .tar.gz file (extracted) it always gives me this

```
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
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
``` 

One thing I DO know Is I need a C compiler.

Any help is appreciated.

---

### Post by cacofonix on 2005-07-15
Have you installed build-essentials? 

```

sudo apt-get install build-essential

```

That should work :)

good luck

cacofonix

---

### Post by master of all on 2005-07-15
Thanks, that worked. But I still get a configure error,

```
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
``` 

What Do i do for this?

---

### Post by McSnickered on 2005-07-15
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=45741](http://ubuntuforums.org/showthread.php?t=45741)

---

