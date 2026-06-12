---
title: "Problem w/Breezy make xconfig or make menuconfig"
date: 2005-10-22
forum: Desktop Environments
---

### Post by athem on 2005-10-22
Hi,

I just installed Breezy on my new Acer 8104 latptop and I'm using the following Hoary-based HOWTO to recompile my kernel (to fix sound/ALSA problems):

[http://ubuntuforums.org/showthread.php?t=43065&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=43065&page=1&pp=10)

When I run:

make xconfig

I get an error message related to my gcc version:

root@ubuntu:/usr/src/linux# make xconfig
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc-3.4: command not found
make[1]: *** [scripts/basic/fixdep] Error 127
make: *** [scripts_basic] Error 2

My version of gcc is 4.02

root@ubuntu:/usr/src/linux# gcc --version
gcc (GCC) 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

I'm new to kernel compilation - any suggestion for how to fx this?

Thanks.

---

### Post by poofyhairguy on 2005-10-22
I moved this to the correct forum. Have a nice day.

---

### Post by mlomker on 2005-10-22
```

sudo apt-get install gcc-3.4

```

---

