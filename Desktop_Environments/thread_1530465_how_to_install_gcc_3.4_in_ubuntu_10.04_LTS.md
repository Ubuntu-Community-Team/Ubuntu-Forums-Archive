---
title: "how to install gcc 3.4 in ubuntu 10.04 LTS"
date: 2010-07-13
forum: Desktop Environments
---

### Post by Kito1980 on 2010-07-13
Hi all,

I need to install gcc 3.4 in ubuntu to compile an old program. However, I can not find it when I use synaptic. 

I've tried to look for the repository where should be gcc-3.4 but I couldn't find it. 

Please.... help. Thanks!

Kito

---

### Post by mildlyAmused on 2010-07-13
In theory this should work

[http://packages.ubuntu.com/hardy/devel/gcc-3.4](http://packages.ubuntu.com/hardy/devel/gcc-3.4)

You may have to tear apart the package and install the files by hand. But that's not so bad right?

---

### Post by Kito1980 on 2010-07-14
Thanks for your help mildlyAmused.

I've also had to install all the others dependences. 

It's solved.

---

### Post by imcensored1 on 2010-08-01
So how did you get around libc6?

when trying to install libc6 i get this

/bin/sh: /lib/libc.so.6: version `GLIBC_2.11' not found (required by /bin/sh)
dpkg: warning: old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/bin/sh: /lib/libc.so.6: version `GLIBC_2.11' not found (required by /bin/sh)
dpkg: error processing libc6_2.7.deb (--install):
 subprocess new post-removal script returned error exit status 1
/bin/sh: /lib/libc.so.6: version `GLIBC_2.11' not found (required by /bin/sh)

Gcc 3.4 won't install without libc6

---

### Post by olawlor on 2010-08-13
The gcc 3.4 from Jaunty seems to just work on ubuntu 10.04 by downloading just three packages: [gcc-3.4-base]("http://packages.ubuntu.com/jaunty/amd64/gcc-3.4-base/download"), [cpp-3.4]("http://packages.ubuntu.com/jaunty/amd64/cpp-3.4/download"), and [gcc-3.4]("http://packages.ubuntu.com/jaunty/amd64/gcc-3.4/download").  (Links are for 64-bit versions; for 32-bit hopefully just grab [gcc-3.4-base]("http://packages.ubuntu.com/jaunty/i386/gcc-3.4-base/download"), [cpp-3.4]("http://packages.ubuntu.com/jaunty/i386/cpp-3.4/download"), and [gcc-3.4]("http://packages.ubuntu.com/jaunty/i386/gcc-3.4/download").) 

You can cleanly "dpkg -i" each package after it's downloaded.  You run the new compiler like "gcc-3.4 foo.c", or more typically "./configure CC=gcc-3.4", and it seems to work for me (in compiling qemu-0.9.0). 

Your already installed compiler is still the default gcc, so the old and new compilers coexist side by side with different names.

---

### Post by jao_madn on 2010-10-27
> **olawlor said:**
> The gcc 3.4 from Jaunty seems to just work on ubuntu 10.04 by downloading just three packages: [gcc-3.4-base]("http://packages.ubuntu.com/jaunty/amd64/gcc-3.4-base/download"), [cpp-3.4]("http://packages.ubuntu.com/jaunty/amd64/cpp-3.4/download"), and [gcc-3.4]("http://packages.ubuntu.com/jaunty/amd64/gcc-3.4/download").  (Links are for 64-bit versions; for 32-bit hopefully just grab [gcc-3.4-base]("http://packages.ubuntu.com/jaunty/i386/gcc-3.4-base/download"), [cpp-3.4]("http://packages.ubuntu.com/jaunty/i386/cpp-3.4/download"), and [gcc-3.4]("http://packages.ubuntu.com/jaunty/i386/gcc-3.4/download").) 

You can cleanly "dpkg -i" each package after it's downloaded.  You run the new compiler like "gcc-3.4 foo.c", or more typically "./configure CC=gcc-3.4", and it seems to work for me (in compiling qemu-0.9.0). 

Your already installed compiler is still the default gcc, so the old and new compilers coexist side by side with different names.

Its seems binutils >=2.20+ must included to install it in ubuntu 10.04.1 server

---

