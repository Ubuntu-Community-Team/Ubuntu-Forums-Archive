---
title: "Qemu 0.9.1 and GCC"
date: 2008-12-29
forum: General Help
---

### Post by lightshayde on 2008-12-29
When I try to compile and install the Qemu Source Code with the terminal, it tells me:
```
WARNING: "gcc" looks like gcc 4.x
Looking for gcc 3.x
gcc 3.x not found!
QEMU is known to have problems when compiled with gcc 4.x
It is recommended that you use gcc 3.x to build QEMU
To use this compiler anyway, configure with --disable-gcc-check
```

I reply with ```
--disable-gcc-check
```

but it tells me that the command is not found.

A screenshot is below. Can you tell me what I'm doing wrong or what I'm misinterpreting? Or could you tell me where the .deb package of QEMU can be found (if there is one)? Or where I could get gcc 3.4.6? I've been looking on [gcc.gnu.org](gcc.gnu.org) but I can't find it.

---

### Post by eBoxNet on 2008-12-29
did you try : ```
./configure --disable-gcc-check
``` ?

---

### Post by lightshayde on 2008-12-29
No, and it works. But now I need SDL or Cocoa for graphical output. And I want graphical output.

The reason I can't use the package manager is because i don't have an internet connection on the computer running Ubuntu. 

I googled both of them, and I'm not sure what is what.

---

### Post by eBoxNet on 2008-12-29
do you need a qemu manager?

[http://www.davereyn.co.uk/](http://www.davereyn.co.uk/)

---

### Post by lightshayde on 2008-12-29
No, I haven't installed it yet. I'm trying to get it to install.

---

