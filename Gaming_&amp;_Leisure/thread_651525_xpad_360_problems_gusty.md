---
title: "xpad 360 problems gusty"
date: 2007-12-27
forum: Gaming &amp; Leisure
---

### Post by bhuthogg on 2007-12-27
hi,

im following this guide [http://ubuntuforums.org/showthread.php?t=588955](http://ubuntuforums.org/showthread.php?t=588955)

but to no success yet,

here what ive done in terminal

brian@hutman:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libosp5 w3c-dtd-xhtml
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
brian@hutman:~$ 
brian@hutman:~$ cd ~/Desktop/xpad360
brian@hutman:~/Desktop/xpad360$ make
make modules -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/brian/Desktop/xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
brian@hutman:~/Desktop/xpad360$ 

brian@hutman:~/Desktop/xpad360$ cat /dev/input/js0
cat: /dev/input/js0: No such device
brian@hutman:~/Desktop/xpad360$ brian@hutman:~/Desktop/xpad360$ sudo make install
cp -f xpad.ko /lib/modules/`uname -r`/kernel/drivers/input/joystick/
brian@hutman:~/Desktop/xpad360$ 

brian@hutman:~/Desktop/xpad360$ sudo ln /usr/src/linux-headers-2.6.22-14-rt /lib/modules/2.6.22-14-rt/build
ln: `/usr/src/linux-headers-2.6.22-14-rt': hard link not allowed for directory

if someone could do a idiots guide for me id be ever so gr8full.

Thanks for readin

Bhuthogg

---

### Post by kaytaro on 2007-12-27
I used this off another thread quoted here for your help. Worked 100% for me.

about 2/3 down on this page.
[http://ubuntuforums.org/showthread.php?t=404577&page=14]("http://ubuntuforums.org/showthread.php?t=404577&page=14")


> **Jojo12a said:**
> To easify the creation of new compiles after kernel updates, I have created a basic module-assistant package. Install it as follows:

```

# first, download [ATTACH]49205[/ATTACH]
# install prerequisites and package (has to be executed wherever you have put the deb
sudo apt-get install module-assistant
sudo dpkg -i xpad360-source_0.0.7_all.deb
# go to the compilation directory
cd /usr/src
# this compiles and installs a new module package
sudo m-a a-i xpad360
```

I also attached the source package ([ATTACH]49206[/ATTACH]) from which I created this. This package could damage your system, kill your cat or set your house on fire, so I don't guarantee anything. It works for me anyway.

---

### Post by bhuthogg on 2007-12-27
wow that made it all so simple :D

Thanx man

---

### Post by kaytaro on 2007-12-28
Ya, I spent a few good hours going through all the post about the 360 controller right before i saw your post. I got my wired controller working 100% but i still cant link my wireless yet.

---

### Post by bhuthogg on 2008-01-02
> **kaytaro said:**
> Ya, I spent a few good hours going through all the post about the 360 controller right before i saw your post. I got my wired controller working 100% but i still cant link my wireless yet.

the wireless uses Integrated 2.4 GHz high-performance wireless technology lets you control the action from up to 30 feet away.

using this it should work [http://www.play.com/Games/PC/4-/3299826/Microsoft-Xbox-360-Crossfire-PC-Peripheral/Product.html](http://www.play.com/Games/PC/4-/3299826/Microsoft-Xbox-360-Crossfire-PC-Peripheral/Product.html)

good luck with that tho:)

---

### Post by DLGirl08 on 2009-12-25
Dunno if anyone is still viewing this thread, let alone anyone who is/ever was developing any 360 controller drivers, but I figured since I tried it and got an error, I'd post it and see if anyone has any answers.

I did everything as instructed for installing, but whilst running the install, it reported:

```
Build of the package xpad360-source failed!
```

Here's the error log:

```
dh_clean                                                                  
/usr/bin/make clean 
make[1]: Entering directory `/usr/src/modules/xpad360'
/usr/bin/make -C /lib/modules/2.6.31-16-generic/build
M=/usr/src/modules/xpad360 clean
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make[1]: Leaving directory `/usr/src/modules/xpad360' 
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/xpad360'
dh_clean
/usr/bin/make clean
make[2]: Entering directory `/usr/src/modules/xpad360'
/usr/bin/make -C /lib/modules/2.6.31-16-generic/build
M=/usr/src/modules/xpad360 clean
make[3]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
make[3]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make[2]: Leaving directory `/usr/src/modules/xpad360'
for templ in
/usr/src/modules/xpad360/debian/xpad360-module-_KVERS_.postinst.modules.in
/usr/src/modules/xpad360/debian/xpad360-module-_KVERS_.postrm.modules.in
/usr/src/modules/xpad360/debian/xpad360-module-_KVERS_.preinst.modules.in
; do \
cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.31-16-generic/g'` ; \
  done  
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in}
${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.31-16-generic/g
;s/#KVERS#/2.6.31-16-generic/g ; s/_KVERS_/2.6.31-16-generic/g ;
s/##KDREV##/2.6.31-16.53/g ; s/#KDREV#/2.6.31-16.53/g ;
s/_KDREV_/2.6.31-16.53/g  ' < $templ > ${templ%.modules.in}; \
  done 
dh_testdir
dh_testroot
dh_clean -k
make KERNEL_SOURCES=/usr/src/linux MODVERSIONS=detect
KERNEL=linux-2.6.31-16-generic
make[2]: Entering directory `/usr/src/modules/xpad360' 
make -C /lib/modules/2.6.31-16-generic/build M=/usr/src/modules/xpad360
modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
CC [M]  /usr/src/modules/xpad360/xpad.o
/usr/src/modules/xpad360/xpad.c: In function ‘xpad_open’:
/usr/src/modules/xpad360/xpad.c:337: error: ‘struct input_dev’ has no member named ‘private’
/usr/src/modules/xpad360/xpad.c: In function ‘xpad_close’:
/usr/src/modules/xpad360/xpad.c:348: error: ‘struct input_dev’ has no member named ‘private’
/usr/src/modules/xpad360/xpad.c: In function xpad_probe’:
/usr/src/modules/xpad360/xpad.c:438: error: ‘struct input_dev’ has no member named ‘cdev’ 
/usr/src/modules/xpad360/xpad.c:439: error: ‘struct input_dev’ has no member named ‘private’
/usr/src/modules/xpad360/xpad.c: In function ‘usb_xpad_init’:
/usr/src/modules/xpad360/xpad.c:517: error: implicit declaration of function ‘info’
make[4]: *** [/usr/src/modules/xpad360/xpad.o] Error 1
make[3]: *** [_module_/usr/src/modules/xpad360] Error 2 
make[3]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make[2]: *** [modules] Error 2
make[2]: Leaving directory `/usr/src/modules/xpad360'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/xpad360'
make: *** [kdist_build] Error 2
```

What did I do wrong? :(

---

### Post by DLGirl08 on 2009-12-26
Ahhh, I finally figured it out...

Since I have Karmic, which is currently having beaucoup issues at supporting older software (especially xpad), I ended up abandoning xpad and instead went with xboxdrv, hosted at [http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

I installed it, but was having trouble running it at first; it kept saying there was no Xbox controller connected. So, I looked in the ReadMe and found a nifty troubleshooting guide (THANK YOU GRUMBEL!!!).

I used

```
lsusb -v
```

and got a list of data giving every usb device on my system, from root hubs to actual attached devices. Turns out my device wasn't being detected because it was the MadCatz 360 controller, and not the Microsoft one. Well, it has an option to force the driver to use a device on a given USB port... So, when attempting to start xboxdrv, this time I used

```
xboxdrv --device-by-id ####:XXXX --type xbox360
```
(where #### is the idVendor and XXXX is idProduct. Type is important; without it, the driver just says that you need to specify the type; if you get it wrong, you could damage something - or maybe it will just fail and give another error message, IDK)...

It gave an output of real-time data coming in from the controller. The LED stopped blinking and when I moved a stick or pressed a button, the data in the console output reflected this.

I do think that there is a --quiet option of some sort, so you may wish to use this as you won't be able to use that console window for anything else, as the data coming in is updated many, many times a second and steals your command line; also, it does take cpu cycles to report the data, so telling it to keep quiet would be good for system performance.

On the other hand, it would serve as immediate confirmation that everything worked if you didn't specify the --quiet switch, and just closed the console window/tab after seeing the output.

---

### Post by kdb424 on 2009-12-29
dlgirl08, you are my god! (coming from an atheist, that means a lot). I got my Guitar hero guitar up fine without going through much, but I bought a controller (regular gamestop brand) for racing games and it wouldnt see it as an xbox controller. I did what you said,

before (guitar):
sudo /home/kdb424/xboxdrv-linux-0.4.9/xboxdrv --silent

after (regular controller):
sudo /home/kdb424/xboxdrv-linux-0.4.9/xboxdrv --device-by-id 0x1bad:0xf016 --type xbox360 --silent

and it reads my new controller. You just saved me $25 USD bu not having to buy an official controller. I owe you!

---

