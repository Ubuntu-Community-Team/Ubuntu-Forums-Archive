---
title: "wired xbox 360 controler for jaunty"
date: 2009-08-17
forum: Gaming &amp; Leisure
---

### Post by insanecrazy4 on 2009-08-17
Today i bought a xbox 360 controller for my computer so i can hopefully play emulated snes and n64 games. I also bought it so i can use with my 360 since that controller is almost broken (so it wasnt wasted money). I am having troubles finding a good tutorial to get one working with jaunty and im wondering if anyone would have a good tutorial they would like to share.

---

### Post by Choose on 2009-08-17
This might be of some help to you 

[https://help.ubuntu.com/community/Xbox360Controller]("https://help.ubuntu.com/community/Xbox360Controller")

good luck with it;)

---

### Post by insanecrazy4 on 2009-08-17
> **Choose said:**
> This might be of some help to you 

[https://help.ubuntu.com/community/Xbox360Controller]("https://help.ubuntu.com/community/Xbox360Controller")

good luck with it;)

i tried that tutorial and i got stuck with this

```
devon@devon-laptop:~/xpad$ make
make modules -C /usr/src/linux-headers-2.6.28-14-generic SUBDIRS=/home/devon/xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-14-generic'
  CC [M]  /home/devon/xpad/xpad.o
/home/devon/xpad/xpad.c: In function ‘xpad_open’:
/home/devon/xpad/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/devon/xpad/xpad.c: In function ‘xpad_close’:
/home/devon/xpad/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/devon/xpad/xpad.c: In function ‘xpad_probe’:
/home/devon/xpad/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/devon/xpad/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/devon/xpad/xpad.o] Error 1
make[1]: *** [_module_/home/devon/xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-14-generic'
make: *** [all] Error 2

```

---

### Post by insanecrazy4 on 2009-08-19
still need help

---

### Post by jackashe on 2009-09-04
me too.  I have intrepid and I followed those directions and I get 

```

make[1]: Entering directory `/usr/src/linux-headers-2.6.27-14-generic'
  CC [M]  /home/jhauser/xpad/xpad.o
/home/jhauser/xpad/xpad.c: In function ‘xpad_open’:
/home/jhauser/xpad/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/jhauser/xpad/xpad.c: In function ‘xpad_close’:
/home/jhauser/xpad/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/jhauser/xpad/xpad.c: In function ‘xpad_probe’:
/home/jhauser/xpad/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/jhauser/xpad/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/jhauser/xpad/xpad.o] Error 1
make[1]: *** [_module_/home/jhauser/xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-14-generic'
make: *** [all] Error 2

```

---

### Post by gamelord12 on 2009-09-12
I'm having the same problem

---

### Post by NovaWasp on 2009-09-12
Get the user space drivers from here:

[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

follow the instructions in the read me and get all of the dependencies.
This command will make get your controller working for N64 games.  I use it in Project 64 in WINE just fine.
sudo ./xboxdrv --trigger-as-button --silent

This will map key board stuff for non joy stick games.

sudo ./xboxdrv      --silent --ui-clear      --dpad-as-button      --ui-buttonmap  a=XK_a,b=XK_b,x=XK_x,y=XK_y,rb=XK_r,lb=XK_l      --ui-buttonmap dl=XK_Left,dr=XK_Right,du=XK_Up,dd=XK_Down

I still need to map the start and back buttons, but that's what I use for supertux and gens/gs.

good luck.

---

### Post by tudor117 on 2009-09-12
Hi, I have the wireless Xbox 360 controller and it works out-of-the-box in Jaunty 64bit!
A good tool to use is Joystick Calibration (jscalibrator).

---

### Post by gamelord12 on 2009-09-13
Will the user space driver load automatically at boot?  I don't want to have to manually open that tool all the time.  Also, I have 64-bit Jaunty, and according to what I read online, if it detected my controller automatically then the joysticks would control the mouse pointer and there would be all kinds of info on it when I run a certain command in the terminal.

---

### Post by tudor117 on 2009-09-14
Mine works out of the box as a joystick. Not as a mouse. jscalibrator shows button presses and axises. It can also calibrate axises and etc.
I tried using my rockband drums with jaunty, hydrogen and joy2key and it worked great! Well up to a certain extent that joy2key imposes.
Try out jscalibrator and see if you can see your controller.

---

