---
title: "Xbox 360 Wireless Gaming Reciever"
date: 2010-02-17
forum: Gaming &amp; Leisure
---

### Post by Crucias on 2010-02-17
Im following [https://help.ubuntu.com/community/Xbox360Controller#The](https://help.ubuntu.com/community/Xbox360Controller#The) (old) Xbox&#8482; Controller

but it puts out the following error, how do i start trouble shooting this? Im trying to get the reciever working so i can use my wireless headset

crucias@Legion:~/xpad$ make
make modules -C /usr/src/linux-headers-2.6.31-19-generic SUBDIRS=/home/crucias/xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
  CC [M]  /home/crucias/xpad/xpad.o
/home/crucias/xpad/xpad.c: In function &#8216;xpad_wireless_connect&#8217;:
/home/crucias/xpad/xpad.c:291: error: implicit declaration of function &#8216;info&#8217;
/home/crucias/xpad/xpad.c: In function &#8216;xpad_open&#8217;:
/home/crucias/xpad/xpad.c:382: error: &#8216;struct input_dev&#8217; has no member named &#8216;private&#8217;
/home/crucias/xpad/xpad.c: In function &#8216;xpad_close&#8217;:
/home/crucias/xpad/xpad.c:408: error: &#8216;struct input_dev&#8217; has no member named &#8216;private&#8217;
/home/crucias/xpad/xpad.c: In function &#8216;xpad_probe&#8217;:
/home/crucias/xpad/xpad.c:496: error: &#8216;struct input_dev&#8217; has no member named &#8216;cdev&#8217;
/home/crucias/xpad/xpad.c:497: error: &#8216;struct input_dev&#8217; has no member named &#8216;private&#8217;
make[2]: *** [/home/crucias/xpad/xpad.o] Error 1
make[1]: *** [_module_/home/crucias/xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'
make: *** [all] Error 2

---

