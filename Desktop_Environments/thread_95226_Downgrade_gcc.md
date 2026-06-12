---
title: "Downgrade gcc"
date: 2005-11-26
forum: Desktop Environments
---

### Post by Termina on 2005-11-26
I've installed gcc 3.4, but 4.0 is still installed.

I've replaced the link /usr/bin/gcc, with one that points to 3.4

Should I apt-get remove gcc-4.0, or is there something else I have to do?

---

### Post by jalanbuntu on 2005-11-26
May be you have to set the CC variable to the gcc version you want to use....
You can find complete guide to downgrade your gcc version [here]("http://ubuntuforums.org/showthread.php?t=65638&highlight=vmware+breezy")
It's about how to install vmware on breezzy, but there is some nice howto about downgrading the gcc

---

### Post by metoo on 2005-11-26
The breezy kernel is compiled with 3.4, so to compile kernel modules you need to switch to 3.4 which is probably explained in the link.
Something like CC=gcc-3.4 or export CC=gcc-3.4 in the shell in which you compile.

Userland programs are compiled with 4.0 .

You can have multiple versions of gcc in parallel on your system. The default is just 4.0 in breezy.

---

