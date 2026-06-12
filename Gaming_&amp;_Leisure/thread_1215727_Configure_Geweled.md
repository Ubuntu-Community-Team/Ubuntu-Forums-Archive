---
title: "Configure Geweled"
date: 2009-07-17
forum: Gaming &amp; Leisure
---

### Post by txwooley on 2009-07-17
I can't configure Geweled for install.  Here is the output to terminal:

```
me:~$ cd '/home/dad/installed junk/gweled-0.7' 
me:~/installed junk/gweled-0.7$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /home/dad/installed: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

and here is part of the config.log file:

```
## ----------- ##

configure:1309: checking for a BSD-compatible install
configure:1364: result: /usr/bin/install -c
configure:1375: checking whether build environment is sane
configure:1418: result: yes
configure:1442: WARNING: `missing' script is too old or missing
configure:1483: checking for gawk
configure:1512: result: no
configure:1483: checking for mawk
configure:1499: found /usr/bin/mawk
configure:1509: result: mawk
configure:1519: checking whether make sets $(MAKE)
configure:1539: result: yes
configure:1707: checking whether to enable maintainer-specific portions of Makefiles
configure:1716: result: no
configure:1746: checking for style of include used by make
configure:1774: result: GNU
configure:1845: checking for gcc
configure:1861: found /usr/bin/gcc
configure:1871: result: gcc
configure:2115: checking for C compiler version
configure:2118: gcc --version </dev/null >&5
gcc (GCC) 4.2.4 (Ubuntu 4.2.4-1ubuntu4)
Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

I don't know that much about this, but want to install Geweled for my kids to play (yes, and me too!)
Any help would be appreciated.

---

### Post by andrewc6l on 2009-07-17
Try renaming 'installed junk' to 'installed_junk' or something else without a space.

---

### Post by txwooley on 2009-07-18
Wow! That's it!  Thanks for the help, but can you tell me why?  Does the empty space throw off the file path or what?  I have just learned an important lesson, but I'm not sure why it's like that.  Thanks again for the solution.

---

### Post by andrewc6l on 2009-07-20
My guess is that part of the compilation assumes the directory name doesn't have a space in it. Then it does something similar to:

someprogram ${directoryname}

which then (when there is a space) ends up:

someprogram /home/foo/installed junk

which is intepreted by someprogram as two arguments instead of a single argument - probably ignoring the second argument.

---

