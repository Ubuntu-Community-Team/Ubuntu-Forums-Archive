---
title: "kernel compiler and gcc mismatch versions"
date: 2005-07-04
forum: Desktop Environments
---

### Post by jeanjan on 2005-07-04
hi,

I have a problem when I try to install a driver which needs compiling, here's the error message :
```
gcc version: version gcc 3.3.5 (Debian 1:3.3.5-8ubuntu2)
gcc version: version gcc 3.3.5 (Debian 1:3.3.5-8ubuntu2)
Make version: GNU Make 3.80
Linker version: GNU ld version 2.15
Kernel compiler: gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
[!] Kernel compiler and gcc seem to be different versions.
Instead, they should be the same. If you have many compilers
installed, you can specify the correct one with command (in bash)
        export CC=kgcc
before trying to install the driver. Replace kgcc with the command
required for compiling kernels (kgcc is often used in Red Hat systems).
``` 
I installed gcc-3.4 and it goes the same :
```
gcc-3.4 version: version gcc 3.4.4 20050209 (prerelease) (Debian 3.4.3-9ubuntu4)
gcc version: version gcc 3.3.5 (Debian 1:3.3.5-8ubuntu2)
Make version: GNU Make 3.80
Linker version: GNU ld version 2.15
Kernel compiler: gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
[!] Kernel compiler and gcc-3.4 seem to be different versions.
Instead, they should be the same. If you have many compilers
installed, you can specify the correct one with command (in bash)
        export CC=kgcc
before trying to install the driver. Replace kgcc with the command
required for compiling kernels (kgcc is often used in Red Hat systems).
``` 
I didn't find any kgcc.
I don't know what command I should use with "export CC=" or if I should use it.

---

### Post by darkpark on 2005-07-04
i'm still new to ubuntu, but perhaps you could run the synaptics package manager to see if it detects any inconsistencies.  additionally, you could try un-installing both versions of gcc and install gcc 4.0.

---

### Post by jeanjan on 2005-07-05
If I want to uninstall gcc-3.3-base synaptic wants to uninstall almost all of the applications I use, it scared me.

---

### Post by jeanjan on 2005-07-10
up up up !

---

### Post by HellRat on 2007-08-22
Did you find a solution to this? I have the exact same problem. Anyone?

---

### Post by jeanjan on 2007-08-24
no, sorry.

---

