---
title: "X problem trying to configure kproftpd"
date: 2006-01-31
forum: Desktop Environments
---

### Post by Mickey1 on 2006-01-31
Have been trying to get a gui to work for me for proftpd 

so i download kproftpd

when i am in terminal and navigate to the folder and perform the ./confogure command 
this is what it tells me
```

checking for Qt... configure: error: Qt-1.4 (headers and libraries) not found. Please check your installation!

```

This is the full text output:
```

:~/Desktop/kproftpd-0.0$ ./configure
loading cache ./config.cache
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for X... libraries /usr/X11R6/lib, headers
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for ranlib... ranlib
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking for main in -lcompat... no
checking for main in -lcrypt... yes
checking for the third argument of getsockname... socklen_t
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for killpg in -lucb... no
checking for Qt... configure: error: Qt-1.4 (headers and libraries) not found. Please check your installation!

```

Have been looking for ways on the net and googling but so far no fix yet 
I have ubunty 5.10 breezy badger

cheers for any help in advance

---

