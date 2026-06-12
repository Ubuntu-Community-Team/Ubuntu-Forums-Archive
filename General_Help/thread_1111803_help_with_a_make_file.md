---
title: "help with a make file?"
date: 2009-03-31
forum: General Help
---

### Post by shateredsoul on 2009-03-31
so i'm trying to get my xbox 360 controllers to work..

I made the file as the directions said to, I made the "make" file and made sure to keep the tabs in there, i even kept the name of the folder as xpad, but when I enter "make" in the terminal I get this:

omar@omar-laptop:~/Desktop/xbox360$ sudo make
make modules -C /usr/src/linux-headers-2.6.27-11-generic SUBDIRS=/home/omar/Desktop/xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/omar/Desktop/xpad/xpad.o
/home/omar/Desktop/xpad/xpad.c: In function ‘xpad_open’:
/home/omar/Desktop/xpad/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/omar/Desktop/xpad/xpad.c: In function ‘xpad_close’:
/home/omar/Desktop/xpad/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/omar/Desktop/xpad/xpad.c: In function ‘xpad_probe’:
/home/omar/Desktop/xpad/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/omar/Desktop/xpad/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/omar/Desktop/xpad/xpad.o] Error 1
make[1]: *** [_module_/home/omar/Desktop/xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'

any ideas where I'm messing up ? Here' is the link, it's under the "compiling and installing the drives" section where i'm stuck

[https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)

---

