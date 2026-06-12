---
title: "installing logitech chillstream game pad"
date: 2007-04-30
forum: Gaming &amp; Leisure
---

### Post by matsoz on 2007-04-30
hi, im having problems with installing the logitech chillstream game-pad.
I have tried the modprobe adi and xpad, but with no luck..

---

### Post by morphx on 2007-05-02
I'm having the same problem.
The device is detected (as it can be seen listed in the hal-device-manager application) but there doesn't seem to be an appropriate driver for it.
I tried the usual (modprobe joydev / adi / xpad / etc...) but nothing works.

Does anyone knows if this gamepad requires some special drivers or is there a particular trick to make it work?

---

### Post by aVirulence on 2007-06-14
Is there any update on this?

---

### Post by janfsd on 2007-06-25
I've got the same problem, i have tried everything, lots of drivers, but nothing seems to work. I would like to know a solution for this..

---

### Post by aVirulence on 2007-06-25
Hi there, you actually need the xbox360 controller driver. Found that out myself after a long time of trying all drivers. You should follow this guide: 

[http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux](http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux)

But instead of using the files in the section "Driver for both Wired and Wireless controllers" use my version:

[http://www.avirulence.org/xpad.c](http://www.avirulence.org/xpad.c) and [http://www.avirulence.org/xpad.h](http://www.avirulence.org/xpad.h) 

Good luck!

---

### Post by vvlist on 2007-06-25
> **aVirulence said:**
> Hi there, you actually need the xbox360 controller driver. Found that out myself after a long time of trying all drivers. You should follow this guide: 

[http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux](http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux)

But instead of using the files in the section "Driver for both Wired and Wireless controllers" use my version:

[http://www.avirulence.org/xpad.c](http://www.avirulence.org/xpad.c) and [http://www.avirulence.org/xpad.h](http://www.avirulence.org/xpad.h) 

Good luck!

Has anyone tried this driver? I want to buy a gamepad, and that is the one I was looking at.

---

### Post by aVirulence on 2007-06-25
Well, I tried it myself, works really well. I used it with Vendetta Online and ZSNES :)

---

### Post by janfsd on 2007-06-26
Thanks, I am going to try your method now, but I've got some questions: do I still need to patch your files with xpad-360-support-2.6.21.patch?
And another one: Do I have to compile the kernel? Where to get the kernel options showed on the link you posted?

---

### Post by aVirulence on 2007-06-26
No, you don't have to use the patch, if you read it correctly the patch is just another method of getting the xbox 360 controller to work. I misread that myself the first 500 times I tried ;)

Yes, you have to re-compile your kernel. I don't exactly know what tools Ubuntu has for doing this. You should probably get the kernel sources, copy the files I provided into the correct director and follow the Ubuntu documentation on compiling your own kernel. Usually it's easy to use menuconfig, so you can find the options easily. The xbox controller driver and the USB thing is under devices/usb iirc. 

Good luck!

---

### Post by janfsd on 2007-06-26
Ok, I am already doing that, but in the kernel options, I don't have this:
Device Drivers -> USB support -> USB Human Interface Device (full HID) support -> HID input layer support (this cannot be compiled as a module)
The HID input layer support option is missing...
I am using the 2.6.21.5 kernel sources.

EDIT:
Well, I compiled the kernel, but couldn't boot into it :( something must have gone bad...
BTW: using a makefile like this:
```
obj-m := xpad.o
KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS=-I$(shell pwd)

all:
	$(MAKE) modules -C $(KDIR) SUBDIRS=$(shell pwd)

install:
	mv -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/usb/input
```
It installs the file like a kernel module, is it not supposed to give the same result like compiling the kernel from zero, granted that the options for compiling it where the same?

And another thing about your file xpad.c
Am I not supposed to add the bus ID of my controller? It is not in the file. For instance my logitech chillstream controller has this ID 046d:c242

---

### Post by aVirulence on 2007-06-26
The option you are looking for there is Enable support for iBook/Powerbook special keys.

I'm sorry but I actually uploaded the wrong file, you're right, just re-download it, I updated it.. Sorry again..

I think you're right about the makefile, but I'm no expert at it.. 

Good luck!

---

### Post by janfsd on 2007-06-26
Now, it's working!!! No need to re-compile the kernel, just I used the makefile + the files you posted. Thanks for your help! :D

---

### Post by aVirulence on 2007-06-26
Great! 

Now have some fun with it!

---

### Post by arigram on 2007-10-23
Can you assist a total Linux n00b in setting up this gamepad in Ubuntu 7.10 AMD64?

---

### Post by arigram on 2007-10-24
I am sorry to be a bother, but I don't seem to be able to follow the instructions.
Janfsd says that he just used a makefile and those two files aVirulence posted, without recompiling the kernel, but I am not sure how to do it.
I tried to understand and interpret the instructions on the 360 controller link but to no avail.
Can you please help?

---

### Post by samurailink3 on 2007-11-18
I'm having trouble getting my chillstream to work in linux. Can anyone walk me through this? I've used the makefile and the .c and .h files. But I think I'm doing something wrong. Can anyone give me a point by point of what to do? Thanks in advance!!!

---

### Post by samurailink3 on 2007-11-19
My bad... It works! Stupid mistake on my part! Good drivers!

---

### Post by janfsd on 2007-11-19
> **arigram said:**
> I am sorry to be a bother, but I don't seem to be able to follow the instructions.
Janfsd says that he just used a makefile and those two files aVirulence posted, without recompiling the kernel, but I am not sure how to do it.
I tried to understand and interpret the instructions on the 360 controller link but to no avail.
Can you please help?

I just saw your post. Ok in the last version you need to make a change in the makefile I posted.
So 1st download the files provide by avirulance...Create a folder, name it whatever you want, and put the files there. Next inside that folder create a new text file, name it Makefile and put this inside:
```
obj-m := xpad.o
KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS=-I$(shell pwd)

all:
	$(MAKE) modules -C $(KDIR) SUBDIRS=$(shell pwd)

install:
	mv -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick

```
After that, open a terminal and go to that folder, type:
make
sudo make install
You probably will need to restart the computer or just sudo modprobe -r xpad and after sudo modprobe xpad
It should work after.

---

### Post by Darganot on 2007-12-25
Anyone know how to get this working in Quake Wars once the driver is installed?

Is there some kind of way to map the buttons so that I can use this to play flash games?

---

### Post by untouchable on 2007-12-25
Hi everyone, I follow the steps that have put ubuntu but I do not recognize the chillstream not mark any error at compile or anything could help me as I repeated the steps several times but can not help it work :confused::confused::confused:   Help

Pd: Using ubuntu 7.10

---

### Post by untouchable on 2007-12-25
Already settled, :lolflag: combine this method and the other post and runs through :lolflag:
Thanks

---

### Post by janfsd on 2007-12-27
Good that you worked it out. :) That is because the location of the modules changed in the latest kernel.

---

### Post by janfsd on 2007-12-27
> **Darganot said:**
> Anyone know how to get this working in Quake Wars once the driver is installed?

Is there some kind of way to map the buttons so that I can use this to play flash games?

Is it not working at all in Quake wars? Have you tried to use jscalibrator to check if it works?

---

### Post by Darganot on 2007-12-28
> **janfsd said:**
> Is it not working at all in Quake wars? Have you tried to use jscalibrator to check if it works?

No it doesn't respond at all in Quake Wars.  From reading on ETQW forums for now I'll have to map all the buttons in my autoexec.cfg   I tried using an Xbox 360 controller script someone posted but it didn't work.

What's jscalibrator?

---

### Post by acoustibop on 2007-12-28
> **janfsd said:**
> Is it not working at all in Quake wars? Have you tried to use jscalibrator to check if it works?

jscalibrator is a joystick calibration application with a gui.  However, I wouldn't recommend using it except for the version that's integrated into Kubuntu.  That one's apparently Ok, but versions you install through the repositories have a nasty habit of disabling the directional controls of joysticks/game controllers for all other applications, while still reporting them as being fine.

There's also a command line calibrator called joystick in the repositories; it may not be so convenient, but it works.

---

### Post by arigram on 2007-12-28
> **janfsd said:**
> I just saw your post. Ok in the last version you need to make a change in the makefile I posted.
So 1st download the files provide by avirulance...Create a folder, name it whatever you want, and put the files there. Next inside that folder create a new text file, name it Makefile and put this inside:
```
obj-m := xpad.o
KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS=-I$(shell pwd)

all:
	$(MAKE) modules -C $(KDIR) SUBDIRS=$(shell pwd)

install:
	mv -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick

```
After that, open a terminal and go to that folder, type:
make
sudo make install
You probably will need to restart the computer or just sudo modprobe -r xpad and after sudo modprobe xpad
It should work after.

Thank you for the reply but I get an error:
> arigram@Persephone:~/xpad$ make
make modules -C  SUBDIRS=/home/arigram/xpad
make: *** SUBDIRS=/home/arigram/xpad: No such file or directory.  Stop.
make: *** [all] Error 2

---

### Post by janfsd on 2008-01-06
Try to make a new folder and start from the beginning, that is download [http://www.avirulence.org/xpad.c](http://www.avirulence.org/xpad.c) & [http://www.avirulence.org/xpad.h](http://www.avirulence.org/xpad.h)
and create inside that folder Makefile and put what i wrote before inside that. Now try to make again.

---

### Post by horzadome on 2008-02-16
I've had some trouble understanding this thread, and the path in Makefile was wrong for 2.6.24-7-generic kernel, so this is what worked for me. njoy:

1) no need to copy anything to /usr/src directory
2) unplug the joystick (otherwise your computer might explode or something really scarry... like hang while removing xpad kernel module) 
3) in console paste this:
```

mkdir $HOME/joystick
cd $HOME/joystick
wget "http://www.avirulence.org/xpad.c"
wget "http://www.avirulence.org/xpad.h"
wget "http://www.horza.info/projekti/xpad-driver-linux/Makefile"
sudo modprobe -r xpad
make
sudo make install
sudo modprobe xpad
cd $HOME
rm -Rf $HOME/joystick

```

---

### Post by Zalbor on 2008-02-19
I just did this, it worked. Thanks!

But there's a problem: In jscalibrator, it seems to recognize some buttons that don't exist and the axes are recognized wrong -the left stick seems to move the pointer reversedly in the veritcal direction, and other things.

---

### Post by acoustibop on 2008-02-19
See my previous post (about 5 posts previous to this) about jscalibrator, Zalbor.

If you remove jscalibrator (which you should), make sure you remove its configuration as well.

---

### Post by janfsd on 2008-03-02
And don't forget that for each kernel update, you should repeat this process again.

---

### Post by horzadome on 2008-04-26
ok, looks like avirulence is getting a redisign, so links don't work. here is the updated copy/paste code with new links. i'll be maintaining it as long as i use chillstream, so feel free to use it.

```
mkdir $HOME/joystick
cd $HOME/joystick
wget "http://www.horza.info/projekti/xpad-driver-linux/xpad.c"
wget "http://www.horza.info/projekti/xpad-driver-linux/xpad.h"
wget "http://www.horza.info/projekti/xpad-driver-linux/Makefile"
sudo modprobe -r xpad
make
sudo make install
sudo modprobe xpad
cd $HOME
rm -Rf $HOME/joystick
```

---

### Post by aVirulence on 2008-04-26
Oops, forgot I still had those on my website. Thanks for hosting them.

---

### Post by Open on 2008-07-10
Hey horzadome

Is there a way to make this permanent sow I don't have to put in the code every time I want to use my gamepad ?

---

### Post by horzadome on 2008-07-12
> **Open said:**
> Hey horzadome

Is there a way to make this permanent sow I don't have to put in the code every time I want to use my gamepad ?i don't think you should repeat this procedure every time you run your games. just every time you upgrade your kernel. and yes, it's like every week or two on ubuntu ;)

---

### Post by MaltalossEion on 2008-11-19
I just bought a Chillstream and followed the steps in this thred, unfortunaly I can only make the mouse move. In other words: The buttons don't work and I'm clueless on what to do now.

Edit: I followed the steps again and I got this in my terminal:

```
gawain@cradle:~/joystick$ make
make modules -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/gawain/joystick
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/gawain/joystick/xpad.o
/home/gawain/joystick/xpad.c: In function &#8216;xpad_open&#8217;:
/home/gawain/joystick/xpad.c:384: error: &#8216;struct input_dev&#8217; has no member named &#8216;private&#8217;
/home/gawain/joystick/xpad.c: In function &#8216;xpad_close&#8217;:
/home/gawain/joystick/xpad.c:410: error: &#8216;struct input_dev&#8217; has no member named &#8216;private&#8217;
/home/gawain/joystick/xpad.c: In function &#8216;xpad_probe&#8217;:
/home/gawain/joystick/xpad.c:498: error: &#8216;struct input_dev&#8217; has no member named &#8216;cdev&#8217;
/home/gawain/joystick/xpad.c:499: error: &#8216;struct input_dev&#8217; has no member named &#8216;private&#8217;
make[2]: *** [/home/gawain/joystick/xpad.o] Error 1
make[1]: *** [_module_/home/gawain/joystick] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [all] Error 2
gawain@cradle:~/joystick$ sudo make install
mv -f xpad.ko /lib/modules/2.6.27-7-generic/kernel/drivers/input/joystick
mv: cannot stat `xpad.ko': No such file or directory
make: *** [install] Error 1
gawain@cradle:~/joystick$ sudo modprobe xpad

```
((Sorry for bumping this thread. just thought it would be relevant))

---

### Post by samurailink3 on 2008-11-19
Agreed. Just upgraded to Ubuntu 8.10 and the Chillstream only moves the mouse, there is no calibration options. My guess is that this isn't showing up as a joystick at all.

---

### Post by arbosis on 2008-12-06
I have the same problemn with 8.10, the controller only moves the mouse and I haven't found any solution to that yet.

---

### Post by samurailink3 on 2008-12-06
Is there something different about the way 8.10 handles /dev/input/js0 from other versions? I know 8.04 changed the /dev location of joystick devices, but are there different defaults set to this device in 8.10?

---

### Post by Open on 2008-12-17
Hey guys tjeck this out > [https://help.ubuntu.com/community/Joystick_lshal_outputs_done](https://help.ubuntu.com/community/Joystick_lshal_outputs_done)

---

### Post by arbosis on 2008-12-30
> **Open said:**
> Hey guys tjeck this out > [https://help.ubuntu.com/community/Joystick_lshal_outputs_done](https://help.ubuntu.com/community/Joystick_lshal_outputs_done)
**That worked for me, thanks :D**

---

### Post by cchester on 2009-11-10
Hey Guys,

I have a logitech chillstream controller and I am using Ubuntu 9.10 amd64. So all I need to do is copy the fdi file to the directory stated above and reboot and everything should work?

Is that correct?

Also how can i verify that it is work after I do this?

Thanks for any help.

---

### Post by mike5853 on 2010-09-11
I AM LOST... using 10.04

---

### Post by Eternal_Light on 2010-10-27
I am using Kubuntu 10.10. After plugging in my Chillstream xbox360 controller and rebooting my system could detect it normally in /dev/input/js1. During calibration funny things start happening tho. When using analog sticks the mouse gets affected. ie when i bend my 1axis-x to the left the pointer on screen starts sliding to the left as well but when i release the analog stick the pointer keeps hitting against the left border of the screen extremely fast. Same thing happens with most other analogs my pad has (some even simulating the scrollbar making me have to keep Alt pressed down all the time to prevent the desktop switch spam).... Every time I try to recalibrate it i have to do unplug the device or do a reboot to regain control of the mouse. After a fresh reboot, if i have my device plugged but havent touched any analog sticks yet, it lays dormant and everything behaves as it should... 

Sorry for my bad english and thanks for your help :)

---

### Post by fuelnatchos on 2011-01-02
Since the pages referred to with the xpad.c and xpad.h modules are not working anymore, for ubuntu 8.04, I used the xpad.c file from the kernel 2.6.27.57, downloaded from kernel.org ([http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.27.57.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.27.57.tar.bz2)) - I could have used another version but this one worked -. It's inside 'drivers/input/joystick'.

I used the xpad.h file from the sourceforge project:
[http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h](http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h)

I had to use this xpad.c file because the one on xbox-linux sourceforge page didn't work (joystick light flashing and no js1 device created)

---

### Post by Fonix on 2011-10-03
i went here [https://help.ubuntu.com/community/Joystick_lshal_outputs_done](https://help.ubuntu.com/community/Joystick_lshal_outputs_done) but the link specifies that i should copy the .fdi file to /etc/hal/fdi/policy/ but i get this error:

cp: cannot create regular file `/etc/hal/fdi/policy/': No such file or directory

using 11.04

---

