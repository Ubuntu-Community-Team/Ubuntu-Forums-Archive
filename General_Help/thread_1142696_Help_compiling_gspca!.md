---
title: "Help compiling gspca!"
date: 2009-04-29
forum: General Help
---

### Post by tahnok on 2009-04-29
Hello,

I'm trying to get my Microsoft VX-2000 webcam working under Ubuntu and I've seen it being done using gspca. But I just can't seem to build the damn thing!

Every time I try to build it using the bundled script it spits out this.

```
 make -C /lib/modules/`uname -r`/build SUBDIRS=/home/wesley/Desktop/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/wesley/Desktop/gspcav1-20071224/gspca_core.o
/home/wesley/Desktop/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/wesley/Desktop/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/wesley/Desktop/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/home/wesley/Desktop/gspcav1-20071224/gspca_core.c: At top level:
/home/wesley/Desktop/gspcav1-20071224/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/home/wesley/Desktop/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/home/wesley/Desktop/gspcav1-20071224/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/home/wesley/Desktop/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/wesley/Desktop/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/home/wesley/Desktop/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/home/wesley/Desktop/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/wesley/Desktop/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/home/wesley/Desktop/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/wesley/Desktop/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2

```

I think the problem is the first error. It can't seem to find asm/semaphore.asm 

Any ideas on how to fix this?

---

### Post by tahnok on 2009-05-03
Bump

---

### Post by michy99 on 2009-05-03
In /usr/src/linux-headers-2.{whatever kernal you are using}/include/ there are a bunch of directories that start with asm like asm-x86, asm-alpha, asm-spark64, etc. Every one of these has a semaphore.h file. My guess is you need to replace 'asm' in the make file with 'asm-{whatever}' to reflect your architecture. Did you run a configure script before running make?

---

### Post by tahnok on 2009-05-03
I guess I assumed that the script would do a configure first. It's supposed to compile everything, but I'll try it now.

---

