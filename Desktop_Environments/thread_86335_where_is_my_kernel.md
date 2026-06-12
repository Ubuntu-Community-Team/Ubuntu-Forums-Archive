---
title: "where is my kernel"
date: 2005-11-04
forum: Desktop Environments
---

### Post by mxyzptlk on 2005-11-04
well it seems that none of the kernels i have, matches with the kernel my system was compiled (wierd isn't it)

# whereis kernel
kernel: /usr/src/linux-headers-2.6.12-9-686/kernel /usr/src/linux-headers-2.6.12-9/kernel

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.12-9/include

The directory of kernel headers (version 2.6.12-9) does not match your running
kernel (version 2.6.12-9-386). Even if the module were to compile successfully,it would not load into the running kernel.


What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.12-9-686/include

The directory of kernel headers (version 2.6.12-9-686) does not match your
running kernel (version 2.6.12-9-386). Even if the module were to compile
successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]


so those are the messages i got


any suggestion

10x in advanced

---

### Post by SickTwist on 2005-11-04
What are you trying to do?

---

### Post by mxyzptlk on 2005-11-04
I am trying to install VMware

after a few installation procedura that message shows up

---

### Post by Xian on 2005-11-04
Let's see what this produces.
Open a terminal and issue this command:

```
$ sudo apt-get install linux-headers-`uname -r`
```

---

