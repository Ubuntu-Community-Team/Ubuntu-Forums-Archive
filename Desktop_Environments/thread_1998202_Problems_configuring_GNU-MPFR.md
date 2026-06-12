---
title: "Problems configuring GNU-MPFR"
date: 2012-06-06
forum: Desktop Environments
---

### Post by prasanmouli on 2012-06-06
[FONT=Comic Sans MS][SIZE=2]I've  been installing software packages as a part of developing for the AVR  micro-controllers. In the process, I successfully built and installed  gmp-4.3.2
As a next step, I went on to build mpfr.2.4.2 

My command was like:
[FONT=Courier New]prasan@ubuntu:~/Downloads/mpfr-2.4.2$ ./configure --prefix=/usr/local/AVR[/FONT]
[/SIZE][/FONT][FONT=Comic Sans MS]
But I got an error as follows: [/FONT]
......
[FONT=Courier New]checking for gmp.h... no
configure: error: gmp.h can't be found, or is unusable.
[/FONT]
[FONT=Comic Sans MS]I even checked in the /usr/local/AVR/include[/FONT] directory for a gmp.h file and it was there. 
[FONT=Comic Sans MS]Help me please![/FONT]

---

