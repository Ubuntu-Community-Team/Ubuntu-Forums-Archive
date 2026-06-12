---
title: "Xbox 360 Wireless Reciver Ubuntu 9.10 drivers?"
date: 2009-11-03
forum: Gaming &amp; Leisure
---

### Post by FractureX on 2009-11-03
I've been trying to get it to work all day on my fresh install of 9.10 Karmic Koala.
Has anyone got the xpad360 drivers working on 9.10?

---

### Post by rsinha on 2009-11-08
No luck at all! I just purchased an xbox wireless controller, haven't tried it with older versions of ubuntu. With karmic, it does not work at all (the controller never bonds with the receiver). I tried the instructions given here as well but to no avail:
[https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)

Make fails with an error. 

```

ritesh@ritesh-desktop:~/xpad$ make
make modules -C /usr/src/linux-headers-2.6.31-14-generic SUBDIRS=/home/ritesh/xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/ritesh/xpad/xpad.o
/home/ritesh/xpad/xpad.c: In function ‘xpad_wireless_connect’:
/home/ritesh/xpad/xpad.c:291: error: implicit declaration of function ‘info’
/home/ritesh/xpad/xpad.c: In function ‘xpad_open’:
/home/ritesh/xpad/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/ritesh/xpad/xpad.c: In function ‘xpad_close’:
/home/ritesh/xpad/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/ritesh/xpad/xpad.c: In function ‘xpad_probe’:
/home/ritesh/xpad/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/ritesh/xpad/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/ritesh/xpad/xpad.o] Error 1
make[1]: *** [_module_/home/ritesh/xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2


```Would love for it to work with XBMC.

---

### Post by thelamer on 2009-11-28
Running into the same thing. 

Anyone have a 360 wireless controller working in Karmic?

---

### Post by benmoran on 2009-12-09
Mine works in Karmic. I previously used it with 9.04, so the controller was already bonded with the receiver. Try booting from a Jaunty live CD, bonding it there, and then trying it again in Karmic. With the current driver the LED never stops flashing even when it's bonded, FYI.

The way the current xpad driver assigns the joystick axis' and dpad are kind of strange, but i've read that work has already been done to fix a lot of the problems. For example, the LED will now correctly register instead of blinking forever. I don't know if this updated driver will ever make it to Karmic, or maybe Lucid. 

To solve the annoyances above, there is another driver option called xboxdrv. This one works in userspace. I've been trying to compile it, but I keep getting memcpy errors. I gave up on it for the time being, but maybe someone else has better luck.
[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

---

### Post by rsinha on 2009-12-09
Followed the instructions here :

[http://stolennotebook.com/anthony/2008/09/13/using-xbmc-for-linux-with-an-xbox-360-wireless-controller-and-the-userspace-usb-driver-xboxdrv/](http://stolennotebook.com/anthony/2008/09/13/using-xbmc-for-linux-with-an-xbox-360-wireless-controller-and-the-userspace-usb-driver-xboxdrv/)

Works perfectly now!

---

