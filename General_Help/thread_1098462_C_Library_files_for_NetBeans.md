---
title: "C Library files for NetBeans"
date: 2009-03-17
forum: General Help
---

### Post by shailendra on 2009-03-17
Hi Friends,

I installed NetBean for doing some C and C++ programming. I wrote a small C program and when I tried to compile it, I found that the library files such as "stdio.h" files are missing. I searched the whole NetBean folder, but I couldn't find any C library files.

Please let me know how can I get these library files.

Also, I would like to know if there is any other IDE which is specifically designed for C and C++ and which comes with all the library.

I think NetBean is more useful for Java programming.

---

### Post by taurus on 2009-03-17
You need the build-essential package.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by shailendra on 2009-03-22
Hi,

Thanks a lot for your help. I installed "build_essentials", I am now able to compile and run my code.

---

