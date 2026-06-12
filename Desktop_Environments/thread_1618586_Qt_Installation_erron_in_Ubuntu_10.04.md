---
title: "Qt Installation erron in Ubuntu 10.04"
date: 2010-11-10
forum: Desktop Environments
---

### Post by suryaemlinux on 2010-11-10
Hi,
I'm trying to install Qt in my ubuntu 10.04 and I received the following error. 

[B]qvfbshmem.cpp:42:22: error: asm/page.h: No such file or directory
[/B]
What I have to install to remove this error. 

Thanks,

---

### Post by tom4everitt on 2010-11-11
What method are you using to install it?

---

### Post by suryaemlinux on 2010-11-11
I'm trying to install Qt version 4.2.2. I can't install the latest Qt version as 4.2.2 is our legacy system support. I must have to install Qt 4.2.2 on ubuntu 10.04. 

Thanks,

---

### Post by tom4everitt on 2010-11-12
Okay, so you are trying to install it from source, then? Usually there should be some sort of documentation regarding dependencies, did you go through that?

Also, what commands are you running now? Is it
./configure
make
make install

Can you run the configure script without problem, or is it when you do "make" or "make install" that you receive the error?

---

### Post by linux-hack on 2010-11-12
If you have errors when you do make && make install it means you don't have dev tools instaled and you just do a 

```
sudo apt-get install build-essentials
```

---

### Post by suryaemlinux on 2010-11-12
I already have build-essential installed. I even have the soft link for page.h file in "/usr/include/asm.h". I found that asm.h file in, "/usr/src/linux-headers-2.6.32-21/include/asm-generic". But it still says No such file or directory.

---

### Post by linux-hack on 2010-11-15
Try this : ```
sudo apt-get install qt-sdk
```

---

