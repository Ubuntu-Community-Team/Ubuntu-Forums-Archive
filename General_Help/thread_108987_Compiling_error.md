---
title: "Compiling error"
date: 2005-12-27
forum: General Help
---

### Post by pjman on 2005-12-27
I'm trying to compile Truecrypt and i'm getting the following error. Does anyone know how to fix it?

Thanks!


```

user@home:~/downloads/truecrypt-4.1-source-code/Linux$ uname -r
2.6.12-10-686
user@home:~/downloads/truecrypt-4.1-source-code/Linux$ ls -l
total 20
-rwxr--r--  1 travis travis 1992 2005-11-23 15:59 build.sh
drwx------  3 travis travis 4096 2005-11-25 16:54 Cli
drwx------  2 travis travis 4096 2005-11-25 16:54 Common
-rwxr--r--  1 travis travis 2827 2005-11-20 07:50 install.sh
drwx------  3 travis travis 4096 2005-11-25 16:54 Kernel
user@home:~/downloads/truecrypt-4.1-source-code/Linux$ sudo ./build.sh
Checking build requirements...
Error: Kernel source code is incomplete - header file dm.h not found.
user@home:~/downloads/truecrypt-4.1-source-code/Linux

```

---

### Post by jliedeka on 2005-12-27
You probably need to install the kernel source package.  I have 2 files called dm.h.  One is from an OSS sound driver the other is from a raid driver.

---

