---
title: "Asus oled"
date: 2009-06-14
forum: General Help
---

### Post by Azati Prime on 2009-06-14
I'm an utter linux noob so bear with me. I have Ubuntu on my ASUS G1S and the little OLED screen always says ASUS.  In Windows you can change this to a clock or text or just plain turn it off.  I came across a driver to control it but the instructions are woefully inadequate for someone like me.  Can anyone help me out?
**[http://lapsus.berlios.de/asus_oled.html](http://lapsus.berlios.de/asus_oled.html)**

I tried extracting the folder that comes in the download and running make like it suggests in the readme and I just get a string of errors.

> kevin@mint ~/Desktop/asus_oled-0.03 $ sudo make
[sudo] password for kevin: 
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/kevin/Desktop/asus_oled-0.03 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/kevin/Desktop/asus_oled-0.03/asus_oled.o
/home/kevin/Desktop/asus_oled-0.03/asus_oled.c: In function ‘class_set_enabled’:
/home/kevin/Desktop/asus_oled-0.03/asus_oled.c:171: error: implicit declaration of function ‘class_get_devdata’
/home/kevin/Desktop/asus_oled-0.03/asus_oled.c: At top level:
/home/kevin/Desktop/asus_oled-0.03/asus_oled.c:439: error: expected ‘)’ before ‘(’ token
/home/kevin/Desktop/asus_oled-0.03/asus_oled.c:440: error: expected ‘)’ before ‘(’ token
/home/kevin/Desktop/asus_oled-0.03/asus_oled.c: In function ‘asus_oled_probe’:
/home/kevin/Desktop/asus_oled-0.03/asus_oled.c:478: error: implicit declaration of function ‘class_device_create’
/home/kevin/Desktop/asus_oled-0.03/asus_oled.c:479: warning: assignment makes pointer from integer without a cast
/home/kevin/Desktop/asus_oled-0.03/asus_oled.c:486: error: implicit declaration of function ‘class_set_devdata’
/home/kevin/Desktop/asus_oled-0.03/asus_oled.c:488: error: implicit declaration of function ‘class_device_create_file’
/home/kevin/Desktop/asus_oled-0.03/asus_oled.c:488: error: ‘class_device_attr_enabled’ undeclared (first use in this function)
/home/kevin/Desktop/asus_oled-0.03/asus_oled.c:488: error: (Each undeclared identifier is reported only once
/home/kevin/Desktop/asus_oled-0.03/asus_oled.c:488: error: for each function it appears in.)
/home/kevin/Desktop/asus_oled-0.03/asus_oled.c:492: error: ‘class_device_attr_picture’ undeclared (first use in this function)
/home/kevin/Desktop/asus_oled-0.03/asus_oled.c:504: error: implicit declaration of function ‘class_device_remove_file’
/home/kevin/Desktop/asus_oled-0.03/asus_oled.c:508: error: implicit declaration of function ‘class_device_unregister’
/home/kevin/Desktop/asus_oled-0.03/asus_oled.c: In function ‘asus_oled_disconnect’:
/home/kevin/Desktop/asus_oled-0.03/asus_oled.c:528: error: ‘class_device_attr_picture’ undeclared (first use in this function)
/home/kevin/Desktop/asus_oled-0.03/asus_oled.c:529: error: ‘class_device_attr_enabled’ undeclared (first use in this function)
make[2]: *** [/home/kevin/Desktop/asus_oled-0.03/asus_oled.o] Error 1
make[1]: *** [_module_/home/kevin/Desktop/asus_oled-0.03] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2


---

