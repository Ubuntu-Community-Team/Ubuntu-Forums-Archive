---
title: "[SOLVED] Problem with  libg2c.so.0  library"
date: 2006-07-30
forum: Desktop Environments
---

### Post by Fingolfin on 2006-07-30
I downloaded executables for ccx and cgx from [www.calulix.de](www.calulix.de) and placed them in /usr/local/bin.
When I attempt to run calculix with % ccx the following message appears:

ccx: error while loading shared libraries: libg2c.so.0: cannot open shared
object file: No such file or directory.

I then went to Synaptic and found the following two files which I installed:
libg2c.so.0 
libg2c.so.0-dev

but the same message appears again when I try to run the program.
The command
% ls -l /usr/lib/libg2c.*

lrwxrwxrwx 1 root root     15 2006-07-30 19:57 /usr/lib/libg2c.so.0 ->
libg2c.so.0.0.0

-rwxr-xr-x 1 root root 120664 2006-03-16 00:47 /usr/lib/libg2c.so.0.0.0

shows that the file does exist in  /usr/lib but that's about all I can tell.

Reinstalling various version of libg2c didnt help unfortunately.

I then tried to compile calculix from source but thata didnt work too.
If someone managed to compile calculix on Ubuntu 6.06, can you please offer some help? 
Is there any specific action that needs to be taken for 64/bit Ubuntu and how exactly should ARPACK and SPOOLES.2.2 libraries be installed (or simply unpacked as source) prior to the compilation itself (maybe that's what I am doing wrong).

This is what I get at the end when the compilation ends with an error:


g77 -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -c writesummary.f
f771: warning: command line option "-Wstrict-prototypes" is valid for C/ObjC but not for F77
cc -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -c arpack.c
cc -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -c arpackbu.c
cc -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -c arpackcs.c
cc -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -c calcresidual.c
In file included from calcresidual.c:21:
CalculiX.h:34: error: syntax error before ‘(’ token
CalculiX.h:138: error: syntax error before ‘(’ token
CalculiX.h:148: error: syntax error before ‘(’ token
CalculiX.h:218: error: syntax error before ‘(’ token
CalculiX.h:241: error: syntax error before ‘(’ token
CalculiX.h:287: error: syntax error before ‘(’ token
CalculiX.h:327: error: syntax error before ‘(’ token
CalculiX.h:375: error: syntax error before ‘(’ token
CalculiX.h:387: error: syntax error before ‘(’ token
CalculiX.h:396: error: syntax error before ‘(’ token
CalculiX.h:401: error: syntax error before ‘(’ token
CalculiX.h:403: error: syntax error before ‘(’ token
CalculiX.h:409: error: syntax error before ‘(’ token
CalculiX.h:703: error: syntax error before ‘(’ token
CalculiX.h:708: error: syntax error before ‘(’ token
CalculiX.h:711: error: syntax error before ‘(’ token
CalculiX.h:796: error: syntax error before ‘(’ token
CalculiX.h:801: error: syntax error before ‘(’ token
CalculiX.h:891: error: syntax error before ‘(’ token
calcresidual.c: In function ‘calcresidual’:
calcresidual.c:63: warning: implicit declaration of function ‘FORTRAN’
calcresidual.c:63: error: ‘op’ undeclared (first use in this function)
calcresidual.c:63: error: (Each undeclared identifier is reported only once
calcresidual.c:63: error: for each function it appears in.)
calcresidual.c:63: warning: left-hand operand of comma expression has no effect
calcresidual.c:63: warning: left-hand operand of comma expression has no effect
calcresidual.c:63: warning: left-hand operand of comma expression has no effect
calcresidual.c:63: warning: left-hand operand of comma expression has no effect
calcresidual.c:63: warning: left-hand operand of comma expression has no effect
calcresidual.c:63: warning: left-hand operand of comma expression has no effect
calcresidual.c:63: warning: left-hand operand of comma expression has no effect
calcresidual.c:63: warning: left-hand operand of comma expression has no effect
make: *** [calcresidual.o] Error 1

---

### Post by halfvolle melk on 2006-07-30
Installing 1 of these 2 packages may help you out.
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libg2c.so.0&searchmode=searchfiles&case=insensitive&version=dapper&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libg2c.so.0&searchmode=searchfiles&case=insensitive&version=dapper&arch=i386)

---

### Post by Fingolfin on 2006-07-31
Thank you for reply, package has been installed but the program in question ccx still cant access it.

%ldd /usr/local/bin/ccx
        linux-gate.so.1 =>  (0xffffe000)
        libg2c.so.0 => not found
        libm.so.6 => /lib32/libm.so.6 (0x5557b000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0x5559e000)
        libc.so.6 => /lib32/libc.so.6 (0x555a9000)
        /lib/ld-linux.so.2 (0x55555000)

It says not found, but the file is definitely in /usr/lib 
and points to 
/usr/lib/libg2c.so.0 ->   libg2c.so.0.0.0

Any ideas on why is this happening?

---

### Post by halfvolle melk on 2006-08-01
Erm, sorry, my bad. Try installing **libg2c0-dev** instead of **libg2c0**. That'll probably fix it.

---

### Post by Fingolfin on 2006-08-03
I managed to identify the cause. I was trying to compile 32-bit program on 64-bit Ubuntu Linux for which these libraries (although with the same name) are different from what the 32-bit program expected to find. 
Everything worked fine on 32-bit Ubuntu.

---

