---
title: "Saitek P2500 - Digital pad doesn't work under MAME"
date: 2007-11-25
forum: Gaming &amp; Leisure
---

### Post by chriswyatt on 2007-11-25
Hi, I have a Saitek P2500 and I can get it to work fine under ZSNES (digital pad and both analogue sticks all work independently) but under MAME the digital pad doesn't work.  I've tried to set this in the game by pressing tab during the game but it doesn't detect the digital pad.

I downloaded a driver which looked like the answer to my problem but sadly I couldn't install it and I'm a bit of a n00b in the Linux world.

Here are the results I got when I ran $make on the driver

```
make -C /lib/modules/2.6.22-14-generic/build M=/home/chrisw/Desktop/SP2500 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/chrisw/Desktop/SP2500/saitek_p2500.o
/home/chrisw/Desktop/SP2500/saitek_p2500.c:38:26: error: linux/config.h: No such file or directory
/home/chrisw/Desktop/SP2500/saitek_p2500.c: In function ‘SP2500_input_event’:
/home/chrisw/Desktop/SP2500/saitek_p2500.c:241: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/chrisw/Desktop/SP2500/saitek_p2500.c: In function ‘SP2500_upload_effect’:
/home/chrisw/Desktop/SP2500/saitek_p2500.c:291: error: ‘struct input_dev’ has no member named ‘ff_effects_max’
/home/chrisw/Desktop/SP2500/saitek_p2500.c:395: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/chrisw/Desktop/SP2500/saitek_p2500.c:396: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/chrisw/Desktop/SP2500/saitek_p2500.c:397: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/chrisw/Desktop/SP2500/saitek_p2500.c: In function ‘SP2500_close’:
/home/chrisw/Desktop/SP2500/saitek_p2500.c:467: error: ‘struct input_dev’ has no member named ‘ff_effects_max’
/home/chrisw/Desktop/SP2500/saitek_p2500.c:471: error: ‘struct input_dev’ has no member named ‘ff_effects_max’
/home/chrisw/Desktop/SP2500/saitek_p2500.c: In function ‘SP2500_flush’:
/home/chrisw/Desktop/SP2500/saitek_p2500.c:485: error: ‘struct input_dev’ has no member named ‘ff_effects_max’
/home/chrisw/Desktop/SP2500/saitek_p2500.c: In function ‘SP2500_process_packet’:
/home/chrisw/Desktop/SP2500/saitek_p2500.c:509: warning: implicit declaration of function ‘input_regs’
/home/chrisw/Desktop/SP2500/saitek_p2500.c: In function ‘SP2500_probe’:
/home/chrisw/Desktop/SP2500/saitek_p2500.c:660: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/chrisw/Desktop/SP2500/saitek_p2500.c:667: error: incompatible types in assignment
/home/chrisw/Desktop/SP2500/saitek_p2500.c:677: error: ‘struct input_dev’ has no member named ‘upload_effect’
/home/chrisw/Desktop/SP2500/saitek_p2500.c:682: error: ‘struct input_dev’ has no member named ‘ff_effects_max’
/home/chrisw/Desktop/SP2500/saitek_p2500.c: At top level:
/home/chrisw/Desktop/SP2500/saitek_p2500.c:754: error: unknown field ‘owner’ specified in initializer
/home/chrisw/Desktop/SP2500/saitek_p2500.c:754: warning: initialization from incompatible pointer type
make[2]: *** [/home/chrisw/Desktop/SP2500/saitek_p2500.o] Error 1
make[1]: *** [_module_/home/chrisw/Desktop/SP2500] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2

```

Thankyou for your time.

---

### Post by chriswyatt on 2007-11-26
Bump

---

### Post by starcannon on 2008-07-01
I got the Saitek P2500 working:

Code:

sudo apt-get install xserver-xorg-input-joystick

Then if the joystick is plugged in, unplug it, and plug it back in.

Enjoy Mame and possibly other gaming goodness.

Enjoy,

~starcannon

I'm looking for info on how to get this game pad to work in Mame as well.

The Numbered Buttons work, the Digital Pad, and Analog Sticks do not work in:
xmame
kxmame
gmame
sdlmame

If anyone knows of a good guide I'm all ears, my google-fu is only bringing up a very small amount of data, nothing interesting so far, perhaps a grand master google-fu artist could gimme a point in the right direction.

---

