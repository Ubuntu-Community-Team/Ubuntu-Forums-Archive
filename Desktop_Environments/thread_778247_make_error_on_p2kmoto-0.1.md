---
title: "make error on p2kmoto-0.1"
date: 2008-05-01
forum: Desktop Environments
---

### Post by decadude on 2008-05-01
root@adub-laptop:/home/adub/Desktop/p2kmoto-0.1# sh install.sh
sh: Can't open install.sh
root@adub-laptop:/home/adub/Desktop/p2kmoto-0.1# make
make  all-recursive
make[1]: Entering directory `/home/adub/Desktop/p2kmoto-0.1'
Making all in src
make[2]: Entering directory `/home/adub/Desktop/p2kmoto-0.1/src'
/bin/bash ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -c p2kmoto.c
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -g -O2 -c p2kmoto.c  -fPIC -DPIC -o .libs/p2kmoto.o
p2kmoto.c:26:17: error: usb.h: No such file or directory
p2kmoto.c:95: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
p2kmoto.c: In function 'p2k_getDevList':
p2kmoto.c:159: error: 'usb_dev_handle' undeclared (first use in this function)
p2kmoto.c:159: error: (Each undeclared identifier is reported only once
p2kmoto.c:159: error: for each function it appears in.)
p2kmoto.c:159: error: 'udev' undeclared (first use in this function)
p2kmoto.c:171: error: 'usb_busses' undeclared (first use in this function)
p2kmoto.c:171: error: dereferencing pointer to incomplete type
p2kmoto.c:172: error: dereferencing pointer to incomplete type
p2kmoto.c:172: error: dereferencing pointer to incomplete type
p2kmoto.c:179: error: dereferencing pointer to incomplete type
p2kmoto.c:181: error: dereferencing pointer to incomplete type
p2kmoto.c:181: error: dereferencing pointer to incomplete type
p2kmoto.c:183: error: dereferencing pointer to incomplete type
p2kmoto.c:184: error: dereferencing pointer to incomplete type
p2kmoto.c:191: error: dereferencing pointer to incomplete type
p2kmoto.c:192: error: dereferencing pointer to incomplete type
p2kmoto.c:195: error: dereferencing pointer to incomplete type
p2kmoto.c:196: error: dereferencing pointer to incomplete type
p2kmoto.c: In function 'p2k_findDevice':
p2kmoto.c:222: warning: assignment makes pointer from integer without a cast
p2kmoto.c:224: error: dereferencing pointer to incomplete type
p2kmoto.c:228: error: dereferencing pointer to incomplete type
p2kmoto.c:228: error: dereferencing pointer to incomplete type
p2kmoto.c:229: error: dereferencing pointer to incomplete type
p2kmoto.c:229: error: dereferencing pointer to incomplete type
p2kmoto.c: In function 'p2k_connect':
p2kmoto.c:253: error: 'phoneHandle' undeclared (first use in this function)
p2kmoto.c: In function 'p2k_closePhone':
p2kmoto.c:274: error: 'phoneHandle' undeclared (first use in this function)
p2kmoto.c: At top level:
p2kmoto.c:314: error: expected declaration specifiers or '...' before 'usb_dev_handle'
p2kmoto.c: In function 'p2k_sendControl':
p2kmoto.c:318: error: 'dev' undeclared (first use in this function)
p2kmoto.c: In function 'p2k_outData':
p2kmoto.c:358: error: 'phoneHandle' undeclared (first use in this function)
p2kmoto.c:358: warning: passing argument 6 of 'p2k_sendControl' makes pointer from integer without a cast
p2kmoto.c:358: warning: passing argument 7 of 'p2k_sendControl' makes integer from pointer without a cast
p2kmoto.c:358: error: too many arguments to function 'p2k_sendControl'
p2kmoto.c: In function 'p2k_inpSize':
p2kmoto.c:374: error: 'phoneHandle' undeclared (first use in this function)
p2kmoto.c:374: warning: passing argument 6 of 'p2k_sendControl' makes pointer from integer without a cast
p2kmoto.c:374: warning: passing argument 7 of 'p2k_sendControl' makes integer from pointer without a cast
p2kmoto.c:374: error: too many arguments to function 'p2k_sendControl'
p2kmoto.c: In function 'p2k_inpData':
p2kmoto.c:408: error: 'phoneHandle' undeclared (first use in this function)
p2kmoto.c:408: warning: passing argument 6 of 'p2k_sendControl' makes pointer from integer without a cast
p2kmoto.c:408: warning: passing argument 7 of 'p2k_sendControl' makes integer from pointer without a cast
p2kmoto.c:408: error: too many arguments to function 'p2k_sendControl'
make[2]: *** [p2kmoto.lo] Error 1
make[2]: Leaving directory `/home/adub/Desktop/p2kmoto-0.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/adub/Desktop/p2kmoto-0.1'
make: *** [all-recursive-am] Error 2

---

