---
title: "[SOLVED] C standard libraries not found"
date: 2006-07-09
forum: Desktop Environments
---

### Post by saul_2110 on 2006-07-09
I just installed Ubuntu 6.06 and added GCC-4.0 and GCC-4.0 base packages but when I tried to compile the "hello world" as a test, it didn't find the libraries (stdio and stdlib).
Also I used the find command to locate them without luck. Is there something else I need to install to get the gnu c compiler working properly?
Thanks.

---

### Post by blitzd on 2006-07-09
> **saul_2110 said:**
> I just installed Ubuntu 6.06 and added GCC-4.0 and GCC-4.0 base packages but when I tried to compile the "hello world" as a test, it didn't find the libraries (stdio and stdlib).
Also I used the find command to locate them without luck. Is there something else I need to install to get the gnu c compiler working properly?
Thanks.

Try this:

sudo apt-get install build-essential

I think it should cover any packages you need for compiling C/C++ programs.

---

### Post by saul_2110 on 2006-07-09
I worked. Thank you.

---

