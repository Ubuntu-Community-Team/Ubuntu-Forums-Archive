---
title: "gamepads, control pads"
date: 2006-11-14
forum: Gaming &amp; Leisure
---

### Post by Somenoob on 2006-11-14
Would it be easy to connect it? and get it functioning properly? has anyone done this before wit their Ubuntu box? 

This would more comfortbale with ZSNES. Thanks in advance.

---

### Post by po0f on 2006-11-14
Somenoob,

It depends on what kind of gamepad/controller it is.  I have my Xbox 360 controller working flawlessly under Edgy.  It works like a champ for zsnes and ePSXe.

Was there a specific question or issue you are having, or just more of a general inquiry?

---

### Post by Somenoob on 2006-11-14
> **po0f said:**
> Somenoob,

It depends on what kind of gamepad/controller it is.  I have my Xbox 360 controller working flawlessly under Edgy.  It works like a champ for zsnes and ePSXe.

Was there a specific question or issue you are having, or just more of a general inquiry?

Xbox 360 controlers work with PCs?

What i am realy trying to avoid are driver problems. I was wondering what manufacturer you recommend, something of high quality and can run under my Dapper system.

---

### Post by po0f on 2006-11-14
Somenoob,

The wired ones do.  If you don't already own one, I can heartily recommend them.  They are actually really great controllers.

---

### Post by Somenoob on 2006-11-14
> **po0f said:**
> Somenoob,

The wired ones do.  If you don't already own one, I can heartily recommend them.  They are actually really great controllers.

Yes but does it not require certain software to run under your system? or are the avrage wired once just plug and play?

---

### Post by Somenoob on 2006-11-14
Just bought an Playstation-like Logitech controller, and it's working properly. anyway, thanks.

---

### Post by edemark on 2006-11-14
which one you bought? just in case I am getting one

---

### Post by Somenoob on 2006-11-14
> **edemark said:**
> which one you bought? just in case I am getting one

It's from Logitech. 

Model name: Rumblepad 2. 

It is very comfotbale, a copy of the modern PlayStation controler. It worked with out any trouble, I just needed to plug it in.

---

### Post by edemark on 2006-11-14
thanks will have a look

---

### Post by po0f on 2006-11-14
You'll have to [compile a kernel module](http://www.ubuntuforums.org/showthread.php?t=164040&highlight=xbox+360+kernel+module), but other than that, the 360 controller is awesome.  If you do go the xpad360 route, let me know if you need help.

---

### Post by dk5151 on 2006-11-15
I can't get my 360 controller to work under Edgy, I tried the tutorial that tells you how to do it without compiling, but no luck. How'd you get yours going?

---

### Post by po0f on 2006-11-15
dk5151,

Can you post, step by step, what you tried to do?

---

### Post by dk5151 on 2006-11-16
Sure. I followed [this tutorial]("http://www.ubuntuforums.org/showthread.php?t=164040&highlight=xbox+360+kernel+module").

1. mkdir ~/xpad360
2. download xpad.c and xpad.h from the gentoo article into ~/xpad360
3. save the following as ~/xpad360/Makefile:

KERNEL_DIR?=/usr/src/linux-headers-2.6.17-10

obj-m := xpad.o

EXTRA_CFLAGS= -I$(shell pwd)

all:
$(MAKE) modules -C $(KERNEL_DIR) SUBDIRS=$(shell pwd)

4. run make in ~/xpad360
5. sudo cp ~/xpad360/*.ko /lib/modules/$(uname -r)/kernel/drivers/usb/input
6. sudo depmod -a
7. sudo modprobe xpad 

I then rebooted and plugged in the controller. The green light just keeps on spinning like before. I'm going to give it another try right now to make sure that I didn't miss a step.

---

### Post by po0f on 2006-11-16
dk5151,

You didn't receive *any* errors?  Is this a Microsoft controller, or a 3rd party controller?

---

### Post by dk5151 on 2006-11-16
-I just tried again, and I am getting some errors now. I must have done something wrong the first time around. I was getting an error, so I followed a suggestion in the tutorial, to change the Makefile to:


KERNEL_DIR?=/usr/src/linux-headers-2.6.17-10-386

obj-m := xpad.o

MKDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS= -I$(shell pwd)

all:
	$(MAKE) modules -C $(MKDIR) SUBDIRS=$(shell pwd)


-When I get to step 4 and run a make while in ~/xpad360, it tells me:

make modules -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/koabel/xpad360
make: *** /lib/modules/2.6.17-10-386/build: No such file or directory.  Stop.
make: *** [all] Error 2


-So I used mkdir to create the build directory, and now it's telling me: 

make modules -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/koabel/xpad360
make[1]: Entering directory `/lib/modules/2.6.17-10-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.17-10-386/build'
make: *** [all] Error 2

Any suggestions?

---

### Post by dk5151 on 2006-11-16
And it's a 3rd party controller, Madcatz.

---

### Post by po0f on 2006-11-16
dk5151,

You're missing your kernel headers; run this from a terminal and try again:
```
$ sudo aptitude update
$ sudo aptitude install linux-headers-`uname -r`
```

Copy and paste that last line if you don't know how to type backticks (`).

---

### Post by dk5151 on 2006-11-16
-Thanks for hanging with me, when I get my headers I get this in the terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

-It looks like it didn't get anything, I may have already done this while trying to get it to work before. Either way, the error message remains the same as my previous post. In my /usr/src directory there are three sets of headers, is something in the process is mixing them up? Unfortunately I'm not experienced enough yet to know. There are "linux-headers-2.6.17-10", "linux-headers-2.6.17-10-386", and "linux-headers-2.6.17-10-generic". 386 is the kernel I'm using.

---

### Post by po0f on 2006-11-17
dk5151,

I guess try installing linux-source-`uname -r` as well as the headers.  I don't recall having to install the source to get this working, but I did have the sources installed.

---

### Post by DirtDawg on 2006-11-17
Following the *second* thread on [this post]("http://www.ubuntuforums.org/showthread.php?t=297361&highlight=joystick+howto") took about 2 minutes and worked great for me. I'm not sure it will work with a 360 controller, it might. I suppose it's up to you if that's worth compiling a kernel. This quick 'n' easy method worked perfectly when I was attaching a Microsoft Sidewinder controller to an Apple iMac(!).

---

### Post by po0f on 2006-11-17
DirtDawg,

That how-to will *not* work for 360 controllers because you *have* to compile a kernel *module*, not a kernel.  Thanks.

---

### Post by DirtDawg on 2006-11-17
> **po0f said:**
> DirtDawg,

That how-to will *not* work for 360 controllers because you *have* to compile a kernel *module*, not a kernel.  Thanks.

Okay, thanks for the clarification.

---

### Post by dk5151 on 2006-11-17
Any idea on my situation? Is it something with my headers?

---

### Post by po0f on 2006-11-17
dk5151,

Look up a couple of posts.  Hint: linux-source-`uname -r`.

---

### Post by dk5151 on 2006-11-18
Ok, I did a fresh install (I've been meaning to do it, had no relation to this project). I went through all of the steps, plus downloaded the linux-source, and I didn't get any errors. The make worked fine once I added the tab to the Makefile, and the rest of the steps went off without a hitch. It didn't seem to do anything though. I rebooted and inserted the controller, and the ring of light is still just blinking. Maybe the module isn't automatically loading? How would I do it manually?

---

### Post by dk5151 on 2006-11-18
I figured out that the last step is how to load the module, modprobe. Still no dice, does this not work with third party controllers?

---

### Post by po0f on 2006-11-18
dk5151,

You can look inside xpad.c to see if your controller model is listed somwhere in there inside a struct.
```

static const struct xpad_device xpad_device[] = {
	/* please keep those ordered wrt. vendor/product ids
	  vendor, product, isMat, name, is360                 */
	{ 0x044f, 0x0f07, 0, "Thrustmaster, Inc. Controller", 0},
	{ 0x045e, 0x0202, 0, "Microsoft Xbox Controller", 0},
	{ 0x045e, 0x0285, 0, "Microsoft Xbox Controller S", 0},
	{ 0x045e, 0x0287, 0, "Microsoft Xbox Controller S", 0},
	{ 0x045e, 0x0289, 0, "Microsoft Xbox Controller S", 0}, /* microsoft is stupid */
	{ 0x045e, 0x028e, 0, "Microsoft Xbox 360 Controller", 1},
	{ 0x046d, 0xca84, 0, "Logitech Xbox Cordless Controller", 0},
	{ 0x046d, 0xca88, 0, "Logitech Compact Controller for Xbox", 0},
	{ 0x05fd, 0x1007, 0, "???Mad Catz Controller???", 0}, /* CHECKME: this seems strange */
	{ 0x05fd, 0x107a, 0, "InterAct PowerPad Pro", 0},
	{ 0x0738, 0x4516, 0, "Mad Catz Control Pad", 0},
	{ 0x0738, 0x4522, 0, "Mad Catz LumiCON", 0},
	{ 0x0738, 0x4526, 0, "Mad Catz Control Pad Pro", 0},
	{ 0x0738, 0x4536, 0, "Mad Catz MicroCON", 0},
	{ 0x0738, 0x4540, 1, "Mad Catz Beat Pad", 0},
	{ 0x0738, 0x4556, 0, "Mad Catz Lynx Wireless Controller", 0},
	{ 0x0738, 0x6040, 1, "Mad Catz Beat Pad Pro", 0},
	{ 0x0c12, 0x8802, 0, "Zeroplus Xbox Controller", 0},
	{ 0x0c12, 0x8809, 0, "Level Six Xbox DDR Dancepad", 0},
	{ 0x0c12, 0x8810, 0, "Zeroplus Xbox Controller", 0},
	{ 0x0c12, 0x9902, 0, "HAMA VibraX - *FAULTY HARDWARE*", 0}, /* these are broken */
	{ 0x0e4c, 0x1097, 0, "Radica Gamester Controller", 0},	
	{ 0x0e4c, 0x2390, 0, "Radica Games Jtech Controller", 0},	
	{ 0x0e6f, 0x0003, 0, "Logic3 Freebird wireless Controller", 0},
	{ 0x0e6f, 0x0005, 0, "Eclipse wireless Controller", 0},
	{ 0x0e6f, 0x0006, 0, "Edge wireless Controller", 0},
	{ 0x0e6f, 0x000c, 0, "PELICAN PL-2047", 0},
	{ 0x0e8f, 0x0201, 0, "SmartJoy Frag Xpad/PS2 adaptor", 0},
	{ 0x0f30, 0x0202, 0, "Joytech Advanced Controller", 0},
	{ 0x0f30, 0x8888, 0, "BigBen XBMiniPad Controller", 0},
	{ 0x102c, 0xff0c, 0, "Joytech Wireless Advanced Controller", 0},
	{ 0x12ab, 0x8809, 1, "Xbox DDR dancepad", 0},
	{ 0xffff, 0xffff, 0, "Chinese-made Xbox Controller", 0}, /* WTF are device IDs for? */
	{ 0x0000, 0x0000, 0, "nothing detected - FAIL", 0}
};
```

---

### Post by leohart on 2006-11-28
I have heard that most people have a good experience with brand-name-for-PC gamepad. Something like the RumblePad 2 of Logitech (currently sells for sub $30 shipped with Google Checkout at Buy.com). I personally prefer these Logitech ones since they feel very nice and very similar to PS2 controllers (which is a plus if you are planning on playing games for extended period).

I am not sure about the different in ease-of-setting-up between the wired and the wireless version of this.

---

### Post by hanzomon4 on 2006-11-29
Is their any hope of getting an xobx360 clone(like the Pelican tsz) to work?

---

### Post by leech on 2006-11-29
The gamepad I use is a Thrustmaster Firestorm Dual Power 3.  I love it, the feel, the fact that it has exactly the same amount of buttons that a Playstation 2 controller has (for either emulators or the games that are crappy Playstation 2 ports on the PC.

Very nice plastic, feels almost like a soft rubber.

Unfortunately they don't make them anymore!  I even had the force feedback working on it at one point (unfortunately the support is experimental and not compiled into the Ubuntu kernel, so you have to compile a custom one (if anyone is interested, I can write a quick tutorial, it's easy with Debian's utilities).  Not much uses the force feedback in Linux yet though.

Generally most input devices (Keyboards, Joysticks, Mice, Gamepads, etc) follow USB HID guidelines, so drivers are pretty universal as far as the PC made game controllers go.  For instance, the Iforce driver supports everything from steering wheels, to joysticks to game pads.  I think there is even a forcefeedback mouse that probably works under it.

Most game pads / Joysticks / Steering wheels will work without issue (now that Udev in Edgy finally seems to be fixed.  Not sure if they finally fixed it in Dapper where you had to change permissions all the time, even after supposedly fixing Udev itself...)

Leech

---

### Post by drocra on 2006-12-01
Hey dk5151, I was having the same problem with my headers. I'm glad you got it working with the fresh install. Just so you know how I ended up fixing it, it turns out I had some other linux-headers installed in addition to my 386 one. I uninstalled all of them, reinstalled the 386, and it worked perfectly.

---

### Post by GeoMX on 2006-12-02
Has anyone made it work for a Xbox (not 360) controller in Edgy?

---

### Post by po0f on 2006-12-02
GeoMX,

You should be able to plug and play with that controller.  Open up a terminal and type the following command:
```
[FONT="Courier New"]$ tail -f /var/log/messages[/FONT]
```
Now plug in your Xbox controller.  It should say something about a new USB device, and something about xpad.c.  If it does, you're golden.  To make sure it works, Ctrl-C to kill the tail command and:
```
[FONT="Courier New"]$ cat /dev/input/js0[/FONT]
```
(It might not be js0 for whatever reason, after typing js, just hit tab.)  Move the sticks around, push some buttons.  Gibberish should pop up on the screen.  Ctrl-C, open up your game and set the controller up.  Have fun!  :)

PS:  If you don't have fun (with the controller), post back.  I can't help you get better games.  ;)

---

### Post by GeoMX on 2006-12-03
I didn't know this controller worked plug&play :). I'm using it with frozen-bubble and zsnes, but it does not work with mupen64 (incorrect behaviour).

Thanks a lot po0f.

---

### Post by po0f on 2006-12-03
GeoMX,

What problems are you having with Mupen64?  I remember using Mupen64 at one point, and had both my Xbox and 360 controllers working.

---

### Post by GeoMX on 2006-12-05
I tried with Mario 64, mapped like this:

Z: L trigger
R: R trigger
Analog stick: left stick
C buttons: right stick
Digital pad: pad
Start: Start
A: A
B: X

The analog stick y-axis seems to be inverted, and pressing the Z buttonresults in a kind of A + Z (jump and smash).

---

### Post by po0f on 2006-12-05
GeoMX,

Sounds like a calibration problem.  Try recalibrating it.  If you want the triggers to act like buttons, when you go to calibrate the triggers, make sure that the minimum and centered values are the same.  Recalibrating should also fix your inverted Y-axis on the left stick as well.

---

### Post by GeoMX on 2006-12-05
Do I calibrate in the emulator or using a separte tool? Thanks.

---

### Post by po0f on 2006-12-05
GeoMX,

Outside the emulator.  I use [jscalibrator](http://packages.ubuntu.com/edgy/x11/jscalibrator), you may have to enable the universe repos to install it if you haven't already

---

### Post by GeoMX on 2006-12-05
I've managed to invert the y-axis using jscal, I moved it up when it asked for its minimum and down when asked for the maximum. Now I just need to fix that weird behaviour with the left trigger :). It seems that mupen64 can map the same input to several buttons/axis, when showing the Z-button mapping it shows:

Key: none
Button: 9
Hat: none
Axis: Z Axis +
Mouse Btn: None

But that Z Axis + appears in some other buttons (L-button and A-Button), and I guess that's why, when pressing the L-trigger in my Xbox controller it works as if I pressed several buttons one after another. The problem is that I haven't found a way to reset/delete the controller mapping.

Thanks a lot for all of your help :).
------------------------------
Edit: I found the input configuration file: blight_input.conf, it's located within my home directory (I was looking for ~/.mupen64 or something like that :P). I edited it and deleted the references to more than one button/axis, now it works well! :D.

Thanks,
JJ (GeoMX).

---

### Post by joshuachild on 2006-12-09
> **po0f said:**
> Somenoob,

It depends on what kind of gamepad/controller it is.  I have my Xbox 360 controller working flawlessly under Edgy.  It works like a champ for zsnes and ePSXe.

Was there a specific question or issue you are having, or just more of a general inquiry?

Could you point me in the right direction on how to get my 360 gamepads working on my Ubuntu Box.

---

### Post by po0f on 2006-12-09
I followed [this](http://ubuntuforums.org/showthread.php?t=164040) tutorial, with a modified Makefile.  First, save this file as ~/xpad360/Makefile:
```
[FONT="Courier New"]obj-m := xpad.o
KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS=-I$(shell pwd)

all:
    $(MAKE) modules -C $(KDIR) SUBDIRS=$(shell pwd)

install:
    cp xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/usb/input[/FONT]
```
The lines after "all:" and "install:" should begin with a tab.

Now, execute these commands from a terminal:
```
[FONT="Courier New"]$ sudo aptitude install build-essential linux-headers-`uname -r` linux-source-`uname -r`
$ cd ~/xpad360
$ wget http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c
$ wget http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h
$ make && sudo make install[/FONT]
```

HTH.

---

### Post by kurros on 2006-12-14
I was able to get the new .ko built but apparently it doesn't work with 2.6.19. Has anyone had any luck?

---

### Post by po0f on 2006-12-14
kurros,

I would just download the xpad source and header files right into your kernel source directory and compile it from there.  You are already compiling the whole kernel, why not throw in another module.  ;)

---

### Post by nexus_2006 on 2006-12-23
> **po0f said:**
> GeoMX,

Sounds like a calibration problem.  Try recalibrating it.  If you want the triggers to act like buttons, when you go to calibrate the triggers, make sure that the minimum and centered values are the same.  Recalibrating should also fix your inverted Y-axis on the left stick as well.

I have the original xbox controller working and jscalibrate installed (both very easy with Dapper)  I still cannot get the triggers to operate as buttons in ZSNES (which is the only joystick-using game I have right now).  Is there somthing simple I am missing?  Also, it registers the D-pad as 2 more axes.  I would like to be able to use them as buttons, if possible.  Any help would be greatly appreciated.

---

