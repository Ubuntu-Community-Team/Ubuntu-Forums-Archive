---
title: "Can't compile in 8.04 Server"
date: 2009-04-22
forum: General Help
---

### Post by flatulent on 2009-04-22
I am getting the following error when I try to configure:

```
$ ./configure
-bash: ./configure: /bin/sh: bad interpreter: Permission denied
```

Sometimes I get this:
```
$ sudo ./configure
sudo: unable to execute ./configure: Permission denied
```

I have installed build-essential:
```

$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.2 --program-suffix=-4.2 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
```

It is not the source tar file, as I have tried an arbitrary sourceforge project and got the same result.

I checked the shell and it looks like this:
```
$ls -al /bin/sh*
lrwxrwxrwx 1 root root 4 2009-04-19 17:42 /bin/sh -> dash
lrwxrwxrwx 1 root root 4 2009-04-19 17:42 /bin/sh.distrib -> bash

```

I tried switching to bash, same result.

Is there some kind of group like sudoers that only they can compile on the 8.04LTS Server

Thanks!
Norm

---

### Post by juancarlospaco on 2009-04-22
use **/bin/bash**, use **sudo**

---

### Post by flatulent on 2009-04-23
As I noted, I tried switching the link to /bin/bash with no change. I also ran it with and without sudo. Permission denied.

Switching to Gentoo. :)

Thanks!

---

### Post by Tim Sharitt on 2009-04-23
Try:

```
chmod +x configure
```

---

