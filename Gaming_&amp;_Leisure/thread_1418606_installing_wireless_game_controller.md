---
title: "installing wireless game controller"
date: 2010-02-28
forum: Gaming &amp; Leisure
---

### Post by rflores2323 on 2010-02-28
I just bought the microsoft wireless game controller.  I am trying to follow this guide to install on ubuntu 9.10.

[https://help.ubuntu.com/community/Xbox360Controller?highlight=%28%28Xbox360Controller%29%29](https://help.ubuntu.com/community/Xbox360Controller?highlight=%28%28Xbox360Controller%29%29)

I have made the directory and have three files in it 

[IMG]http://www.ubuntu-pics.de/bild/44580/screenshot_002_p4hQX0.png[/IMG]

however when I get to the last steps 
```
make
sudo make install
sudo modprobe -r xpad
sudo depmod -a
sudo modprobe xpad
```

I keep getting errors

see below 

```
xbmc@xbmc-desktop:~$ cd /home/xbmc/xpad
xbmc@xbmc-desktop:~/xpad$ sudo make
[sudo] password for xbmc: 
make modules -C /usr/src/linux-headers-2.6.31-19-generic SUBDIRS=/home/xbmc/xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
  CC [M]  /home/xbmc/xpad/xpad.o
/home/xbmc/xpad/xpad.c: In function ‘xpad_wireless_connect’:
/home/xbmc/xpad/xpad.c:291: error: implicit declaration of function ‘info’
/home/xbmc/xpad/xpad.c: In function ‘xpad_open’:
/home/xbmc/xpad/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/xbmc/xpad/xpad.c: In function ‘xpad_close’:
/home/xbmc/xpad/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/xbmc/xpad/xpad.c: In function ‘xpad_probe’:
/home/xbmc/xpad/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/xbmc/xpad/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/xbmc/xpad/xpad.o] Error 1
make[1]: *** [_module_/home/xbmc/xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'
make: *** [all] Error 2
xbmc@xbmc-desktop:~/xpad$ sudo make install
cp -f xpad.ko /lib/modules/2.6.31-19-generic/kernel/drivers/input/joystick
cp: cannot stat `xpad.ko': No such file or directory
make: *** [install] Error 1
xbmc@xbmc-desktop:~/xpad$ sudo modprobe -r xpad
xbmc@xbmc-desktop:~/xpad$ sudo depmod -a
^[[Axbmc@xbmc-desktop:~/xpad$ sudo depmod -a
xbmc@xbmc-desktop:~/xpad$ sudo modprobe xpad
xbmc@xbmc-desktop:~/xpad$ sudo make
make modules -C /usr/src/linux-headers-2.6.31-19-generic SUBDIRS=/home/xbmc/xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
  CC [M]  /home/xbmc/xpad/xpad.o
/home/xbmc/xpad/xpad.c: In function ‘xpad_wireless_connect’:
/home/xbmc/xpad/xpad.c:291: error: implicit declaration of function ‘info’
/home/xbmc/xpad/xpad.c: In function ‘xpad_open’:
/home/xbmc/xpad/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/xbmc/xpad/xpad.c: In function ‘xpad_close’:
/home/xbmc/xpad/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/xbmc/xpad/xpad.c: In function ‘xpad_probe’:
/home/xbmc/xpad/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/xbmc/xpad/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/xbmc/xpad/xpad.o] Error 1
make[1]: *** [_module_/home/xbmc/xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'
make: *** [all] Error 2
xbmc@xbmc-desktop:~/xpad$ sudo cp xpad.ko /lib/modules/$(uname -r)/kernel/drivers/usb/input
cp: cannot stat `xpad.ko': No such file or directory
xbmc@xbmc-desktop:~/xpad$ 


```

Here is my dmesg log also [http://pastebin.com/NPx1NR65](http://pastebin.com/NPx1NR65)

also how do I configure this remote on snes9xpress?  I keep getting this message when I configure the button maps . Why is it showing no file or directory??  what directory do I put?? the xpas directory?

[IMG]http://www.ubuntu-pics.de/bild/44581/screenshot_003_1kUSX6.png[/IMG]

---

### Post by rflores2323 on 2010-03-02
got this to work under zsnes and mupen!

---

