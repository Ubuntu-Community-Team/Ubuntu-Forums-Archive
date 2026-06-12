---
title: "How can I install alsa driver"
date: 2009-01-20
forum: General Help
---

### Post by psychok9 on 2009-01-20
Hello, how can I try the new  alsa-driver-1.0.19 from the sources? I've downloaded: ```
alsa-driver-1.0.19.tar.bz2    alsa-plugins-1.0.19.tar.bz2
alsa-firmware-1.0.19.tar.bz2  alsa-tools-1.0.19.tar.bz2
alsa-lib-1.0.19.tar.bz2

```
But on alsa-driver I got some error on ./configure.
In the past i've compiled Wine correctly, but I'm not expert of compiling ;)
Exist a step by step tutorial for ubuntu?

```
checking for GCC version... ./configure: eval: line 5183: syntax error near unexpected token `)'
./configure: eval: line 5183: `my_compiler_version=4.3.2-1ubuntu11)'
Kernel compiler:  Used compiler: gcc (Ubuntu 4.3.2-1ubuntu11) 4.3.2

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting


```

Thank you.

---

### Post by psychok9 on 2009-01-20
Solved :)
I've found the missing of alsa-utils-1.0.19, following this guide [https://help.ubuntu.com/community/EchoMia](https://help.ubuntu.com/community/EchoMia) and with a little "intuition" (alsa compiling need xmlto package, but aren't visible clear). Now i've installed and it works.

Now can I make .deb package without errors?

---

