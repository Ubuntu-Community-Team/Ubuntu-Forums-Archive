---
title: "Nmap Installation"
date: 2009-02-18
forum: General Help
---

### Post by Enertia on 2009-02-18
Hi,
i am getting the following error while i try to compile nmap. 
Some help?

liblua/liblua.a(loadlib.o): In function `gctm':loadlliblua/liblua.a(loadlib.o): In function `gctm':loadlib.c:(.text+0x2e): undefined reference to `dlclose'
liblua/liblua.a(loadlib.o): In function `ll_loadfunc':loadlib.c:(.text+0xb8): undefined reference to `dlsym'
:loadlib.c:(.text+0x177): undefined reference to `dlerror'
:loadlib.c:(.text+0x1a0): undefined reference to `dlopen'
:loadlib.c:(.text+0x1c1): undefined reference to `dlerror'
collect2: ld returned 1 exit status
make[1]: *** [nmap] Error 1
make[1]: Leaving directory `/home/mrajani/Desktop/nmap-4.22SOC8'
make: *** [all] Error 2
ib.c:(.text+0x2e): undefined reference to `dlclose'
liblua/liblua.a(loadlib.o): In function `ll_loadfunc':loadlib.c:(.text+0xb8): undefined reference to `dlsym'
:loadlib.c:(.text+0x177): undefined reference to `dlerror'
:loadlib.c:(.text+0x1a0): undefined reference to `dlopen'
:loadlib.c:(.text+0x1c1): undefined reference to `dlerror'
collect2: ld returned 1 exit status
make[1]: *** [nmap] Error 1
make[1]: Leaving directory `/home/mrajani/Desktop/nmap-4.22SOC8'
make: *** [all] Error 2

---

### Post by cosine352 on 2009-02-18
what is the command you used ?

---

### Post by snova on 2009-02-18
Why compile from source? Just install the **nmap** package through Synaptic.

---

