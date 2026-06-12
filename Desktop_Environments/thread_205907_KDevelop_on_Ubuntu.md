---
title: "KDevelop on Ubuntu"
date: 2006-06-29
forum: Desktop Environments
---

### Post by solarwind on 2006-06-29
Hello everyone,

How do I get KDevelop working on Ubuntu. I successfully installed KDevelop but when I try to create a simple command line hello world project and try to compile it, the build fails. There is an error about some auto* tools. I think it's the lack of proper development tools in Ubuntu. How do I fix this. I'll post the entire error output if it is needed.

Thanks!

---

### Post by blastradius on 2006-06-29
Try running the Kdevelop setup program. Work through it installing everything that shows up as not found then try your program again.  It should be fine.

---

### Post by solarwind on 2006-06-29
Please reply.

I did a simple c hello world project and went to Build->Build Project. Then I clicked Run Them in the window that popped up.

Here is the error output.



cd '/home/vg/helloworld' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/vg/helloworld/debug' && cd '/home/vg/helloworld/debug' && CFLAGS="-O0 -g3 " "/home/vg/helloworld/configure" --enable-debug=full && cd '/home/vg/helloworld/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
aclocal
aclocal: configure.in: 8: macro `AM_PROG_LIBTOOL' not found in library
make: *** [all] Error 1
*** Exited with status: 2 ***

---

### Post by solarwind on 2006-06-29
How do you run the KDevelop setup program?

---

### Post by solarwind on 2006-07-07
How do you run the KDevelop setup program?

I really need to get KDevelop working.

---

### Post by linuxgoober on 2006-07-18
I have the same problem :-( I should have listened to my friend. He said Gentoo was worth the long install.

---

### Post by EyeOfRa on 2006-07-24
> **solarwind said:**
> Please reply.

I did a simple c hello world project and went to Build->Build Project. Then I clicked Run Them in the window that popped up.

Here is the error output.



cd '/home/vg/helloworld' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/vg/helloworld/debug' && cd '/home/vg/helloworld/debug' && CFLAGS="-O0 -g3 " "/home/vg/helloworld/configure" --enable-debug=full && cd '/home/vg/helloworld/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
aclocal
aclocal: configure.in: 8: macro `AM_PROG_LIBTOOL' not found in library
make: *** [all] Error 1
*** Exited with status: 2 ***

I found a solution on another forum.

sudo apt-get install libtool

It worked for me.  Hope it works for you too.

---

