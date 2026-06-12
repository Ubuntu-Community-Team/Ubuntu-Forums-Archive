---
title: "Can't compile kernel module"
date: 2009-01-01
forum: General Help
---

### Post by koloman.dingus on 2009-01-01
Hi all, I was trying to compile kernel module for communication with CAN devices LinCAN...I didint succeed...
I got only this:
```

[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator
[: 1: ==: unexpected operator

```

aand round and round and round...like an eternal loop or something...

```
laptop:~/ocera/ocera2/components/comm/can$ uname -a
Linux gyre-laptop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
laptop:~/ocera/ocera2/components/comm/can$ 
laptop:~/ocera/ocera2/components/comm/can$ make --version
GNU Make 3.81
laptop:~/ocera/ocera2/components/comm/can$ gcc --version
gcc (Ubuntu 4.3.2-1ubuntu11) 4.3.2

```
Ubuntu InterPID
Does any have any idea how to fix this problem ?
Is it even possible ?
Thanks

---

### Post by dcstar on 2009-01-01
> **koloman.dingus said:**
> Hi all, I was trying to compile kernel module for communication with CAN devices LinCAN...I didint succeed...
I got only this:

[: 1: ==: unexpected operator
.......
Ubuntu InterPID
Does any have any idea how to fix this problem ?
Is it even possible ?
Thanks

And **exactly** what did you do to compile this?

---

### Post by x22 on 2009-01-01
> [: 1: 2: unexpected operator

a suggestion that worked for me was, to look in my 
.config for the line:

CONFIG_ZEN=Y

and either thru one of the make *configs or some
other way, get rid of it.

then as root give the standard Debian compile command

 make-kpkg clean                        
 make-kpkg --initrd kernel_image

this seems to work OK

"the sun is new every day" (heraclitus)

---

