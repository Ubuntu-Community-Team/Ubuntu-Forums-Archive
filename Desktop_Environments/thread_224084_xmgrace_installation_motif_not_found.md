---
title: "xmgrace installation: motif not found"
date: 2006-07-27
forum: Desktop Environments
---

### Post by suxen on 2006-07-27
Hi,
I try to install xmgrace (grace-5.99) under ubuntu-5.10 on amd64.
./configure exits with the following statements:

[INDENT]
...
checking for X... libraries /usr/X11R6/lib, headers
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for _XEditResCheckMessages in -lXmu... yes
checking for main in -lXp... no
checking xpm.h usability... no
checking xpm.h presence... no
checking for xpm.h... no
checking X11/xpm.h usability... yes
checking X11/xpm.h presence... yes
checking for X11/xpm.h... yes
checking for Xpm library >= 30411... yes
checking for a Motif >= 1002 compatible API... no
configure: error: M*tif has not been found
[/INDENT]

I have libmotif3 installed, the so-file is
/usr/X11R6/lib/libXm.so.3.0.2

what can I do?

PS: The same happens when I install xmgrace-latest-stable (5.1.20)

---

