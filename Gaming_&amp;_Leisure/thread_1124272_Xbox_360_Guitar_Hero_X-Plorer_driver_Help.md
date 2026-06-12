---
title: "Xbox 360 Guitar Hero X-Plorer driver Help"
date: 2009-04-13
forum: Gaming &amp; Leisure
---

### Post by cloud4607 on 2009-04-13
Hi all, i need help for compiling the xpad driver on Ubuntu Intrepid... I'm trying, but everytime it shows this error:

```

jd@JDs:~/xpad$ make
make modules -C /usr/src/linux-headers-2.6.27-11-generic SUBDIRS=/home/jd/xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/jd/xpad/xpad.o
/home/jd/xpad/xpad.c: In function ‘xpad_open’:
/home/jd/xpad/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/jd/xpad/xpad.c: In function ‘xpad_close’:
/home/jd/xpad/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/jd/xpad/xpad.c: In function ‘xpad_probe’:
/home/jd/xpad/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/jd/xpad/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/jd/xpad/xpad.o] Error 1
make[1]: *** [_module_/home/jd/xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [all] Error 2

```

Any suggestion on how to fix these errors? Thx in advance...

---

### Post by iTawm on 2009-05-10
I have the same error when trying to install the newer xpad for using 360 controllers...

---

