---
title: "Webcam Driver Installation"
date: 2005-12-17
forum: Desktop Environments
---

### Post by vishnumrao on 2005-12-17
I am trying to install drivers for a creative webcam live pro,  Downloaded the spca5xx drivers as recomended at 

[http://opensource.creative.com/webcam.html](http://opensource.creative.com/webcam.html) 
the following is the content of the readme file:

"This version of the driver offers an automatic installation facility.
Use 'make install' to have the driver installed into your kernel modules
directory, which is assumed to be /lib/modules/<version>/kernel/drivers/usb.
<version> is picked up from the currently running kernel, so if that's not
the right place, then don't use 'make install'!"

while trying to install i get the following error. What am I doing wrong.
vishnumrao@vishnumrao:~/Desktop/spca5xx-20051105$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `spca5xx.ko': No such file or directory
make: *** [install] Error 1

Attached it the read me file for the drivers. Also does gaim have webcam support? 

Thanking you,
Vishnu Rao.

---

### Post by cylon359 on 2005-12-17
Did you run "sudo make" first?

---

### Post by vishnumrao on 2005-12-17
[QUOTE=cylon359]Did you run "sudo make" first?[/QUOTE]

I did sudo make and then sudo make install.


vishnumrao@vishnumrao:~/Desktop/spca5xx-20051105$ sudo make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/vishnumrao/Desktop/spca5xx-20051105 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-amd64-generic'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-amd64-generic'
vishnumrao@vishnumrao:~/Desktop/spca5xx-20051105$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae
vishnumrao@vishnumrao:~/Desktop/spca5xx-20051105$

---

