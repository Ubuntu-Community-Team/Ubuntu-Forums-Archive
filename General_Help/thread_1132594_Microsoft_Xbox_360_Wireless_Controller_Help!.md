---
title: "Microsoft Xbox 360 Wireless Controller Help!"
date: 2009-04-22
forum: General Help
---

### Post by Genics on 2009-04-22
I've been trying to get my Xbox 360 Wireless Controller to work with posts from these forums, I'm getting errors when I try to execute the make in terminal.  I'm trying to get this to work on an Acer Aspire One Laptop with Ubuntu 8.10 with a Microsoft Wireless Receiver and Xbox 360 Wireless Controller.

This is the error I'm receiving in the Terminal, Can anyone help?:

make modules -C /usr/src/linux-headers-2.6.27-11-generic SUBDIRS=/home/genics/xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/genics/xpad/xpad.o
/home/genics/xpad/xpad.c: In function ‘xpad_open’:
/home/genics/xpad/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/genics/xpad/xpad.c: In function ‘xpad_close’:
/home/genics/xpad/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/genics/xpad/xpad.c: In function ‘xpad_probe’:
/home/genics/xpad/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/genics/xpad/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/genics/xpad/xpad.o] Error 1
make[1]: *** [_module_/home/genics/xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [all] Error 2

---

### Post by Genics on 2009-04-22
Fixed my own problem, by searching the forums some more.  This is the solution I found, if anyone else has the same problem...

$ xinput list
See which device number the Xbox controller or xbox Wireless Receiver has
$ xinput set-int-prop THATDEVICENUMBER 'Device Enabled' 32 0

Then all I did was try each number the wireless receiver was, and now it works, but I still have blinking lights on the controller though...

---

### Post by mikeishooligan on 2009-04-22
help!

My controller *was* working (sort of).  Ubuntu detected it out of the box and mupen64 could configure all of the buttons.  However, the left analog stick would move the mouse and I couldn't get mupen to recognize any movements of the left stick.  I tried this fix and now it doesn't recognize my controller at all.  The green led light on the dongle does not light up as it used to.  I've tried rebooting and replugging the dongle to no avail (can you tell i'm a recent windows convert?)

Any help you could provide would be appreciated.

---

