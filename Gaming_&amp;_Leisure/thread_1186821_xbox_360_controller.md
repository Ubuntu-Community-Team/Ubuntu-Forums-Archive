---
title: "xbox 360 controller"
date: 2009-06-13
forum: Gaming &amp; Leisure
---

### Post by tommah04 on 2009-06-13
hey all

I'm a little bummed out cause my xbox 360 controller isn't working on my ubuntu jaunty, when it worked on my friends' out of the box.

I tried using this.... [https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)

but I get to the  "make" portion and I get....

tom@tom-desktop:~/xpad$ make
make modules -C /usr/src/linux-headers-2.6.28-11-generic SUBDIRS=/home/tom/xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/tom/xpad/xpad.o
/home/tom/xpad/xpad.c: In function ‘xpad_open’:
/home/tom/xpad/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/tom/xpad/xpad.c: In function ‘xpad_close’:
/home/tom/xpad/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/tom/xpad/xpad.c: In function ‘xpad_probe’:
/home/tom/xpad/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/tom/xpad/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/tom/xpad/xpad.o] Error 1
make[1]: *** [_module_/home/tom/xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2
tom@tom-desktop:~/xpad$ 

and I get stuck there.

I made sure the Makefile had tabs instead of spaces, so I don't think that's it... I was wondering if anyone had any ideas

xbox 360 wired controller
jaunty amd64

---

### Post by uranus0206 on 2009-06-14
Hi! Though i don't have controller to try.
But you can check this thread.
[http://ubuntuforums.org/showthread.php?t=825464](http://ubuntuforums.org/showthread.php?t=825464)

---

### Post by tommah04 on 2009-06-14
hey,

yea, had a problem with this one too... got up until you create the program with the scons command and I get this....

tom@tom-desktop:~/tmp/xboxdrv-linux-0.2$ scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o uinput.o -c -g -O0 -Wall uinput.cpp
uinput.cpp: In constructor 'uInput::uInput(GamepadType, uInputCfg)':
uinput.cpp:45: error: 'strerror' was not declared in this scope
uinput.cpp:59: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:59: error: 'exit' was not declared in this scope
uinput.cpp:74: error: 'EXIT_FAILURE' was not declared in this scope
uinput.cpp:74: error: 'exit' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_gamepad(GamepadType)':
uinput.cpp:148: error: 'memset' was not declared in this scope
uinput.cpp:149: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::setup_xbox360_guitar()':
uinput.cpp:233: error: 'memset' was not declared in this scope
uinput.cpp:234: error: 'strncpy' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_button(uint16_t, int32_t)':
uinput.cpp:260: error: 'memset' was not declared in this scope
uinput.cpp: In member function 'void uInput::send_axis(uint16_t, int32_t)':
uinput.cpp:274: error: 'memset' was not declared in this scope
scons: *** [uinput.o] Error 1
scons: building terminated because of errors.

---

### Post by tommah04 on 2009-06-15
bump?

---

### Post by tommah04 on 2009-06-18
one more bump

---

### Post by Virginsofcool on 2009-06-20
I'm almost 100% positive this isn't really helpful, but mine worked flawlessly without any modification in Ubuntu Jaunty.  The light on the controller kept flashing like it wouldn't connect, but when I opened zsnes it worked perfect.  I'm running it on a Dell Inspiron B130, so yeah........oh, and I am not using the x64 version.  Mayber others have had problems with that version too.

**Update**
It may depend on the program you are wanting to use it with.  ZSNES works fine, as does Gens and GFCE Ultra, but it doesn't work with VisualBoy Advance.  What are you trying to use it with?

---

### Post by tommah04 on 2009-06-23
yea, my controller only blinks also, but mine doesn't work at all :-\

and I do have 64-bit....so, I'm not sure what to do

---

### Post by tommah04 on 2009-06-23
*sigh* well, not really sure how... but for some reason it just started working....wierd

although I can't get alien arena 2009 to work with it though

---

### Post by JuEUS-U on 2009-07-09
the controller driver in that tutorial(in ubuntu wiki) is a kinda old stuff, written 2 years ago.
because the driver uses some depricated members of input_dev, it can not be compiled for recent kernels. (newer than 2.6.24...? dunno exact version number.)

and,,,, in fact, I fixed those errors by myself and compiled successfully.
but it does not work at all.
it seems kernel cannot recognize the device. :s

---

### Post by puckskraper on 2009-08-04
I found this site but it's in French.  I tried it several times renaming the patches according to the terminal commands listed.  I still get the "..private" errors.  I'm a bit of a noob and using Mythbuntu if anyone can make sense of this please post some English noob friendly instructions, I'd appreciate it.

[http://www.system-linux.eu/index.php?post/2009/06/17/Xpad-et-manette-Xbox360-sur-Debian](http://www.system-linux.eu/index.php?post/2009/06/17/Xpad-et-manette-Xbox360-sur-Debian)

---

### Post by dominichudon on 2009-08-18
Basically, you have to change:

dev->private
to
input_get_drvdata(dev)

input_dev->private = xpad;
to
input_set_drvdata(input_dev, xpad);

input_dev->cdev.dev
to
input_dev->dev.parent

I think it's because they changed the input_dev structure in the newer kernel... I attached a fixed version, I hope it helps.

---

