---
title: "xbox 360 ROCKBAND guitar drivers? FoF"
date: 2008-01-09
forum: Gaming &amp; Leisure
---

### Post by oisuxx on 2008-01-09
i see alot of people asking about guitar hero guitars for the 360 working with frets on fire. but i have the rock band strat model. is there any way to make this work with frets on fire? im trying not to get pushed back to windows for 1 game and its compatibility. can anyone help me out?

i found a few ways to get the X-ploder guitar to work, but i dont have that model.

any help would be appreciated! thanks in advance.

ubuntu 7.10

---

### Post by oisuxx on 2008-01-10
bump.....can anyone help me out?

or even with the rockband DRUMS?

i just wanna not have to install windows for 1 game! :)

---

### Post by 3jd8 on 2008-07-12
I'm not sure about the 360, but my ps2 drums work simply by plugging them in.   Launch jscalibrator and select the appropriate joystick, then click re-open (i think) then smash away.  It should be picking it up.   What i did after that was just map the joystick buttons to keyboard keys.  

Jacob

---

### Post by midkniht on 2008-07-24
Its been working for a few weeks now, the patch was offered to the xbox-linux group and they didnt want it.
The patch is here:
[URL="http://www.jamminnet.com/rockbandguitarandlinux"]http://www.jamminnet.com/rockbandguitarandlinux
[/URL]

It works great, did you really want drum support as well?  I know that he had worked it out but dont know if he actually added it yet.

oh and never threaten to use w**doz just for a game.  linux ftw

> **oisuxx said:**
> bump.....can anyone help me out?

or even with the rockband DRUMS?

i just wanna not have to install windows for 1 game! :)

---

### Post by MyKal on 2008-10-01
AWESOME 

thanks so much it worked for me :) :guitar::guitar::guitar: :)

---

### Post by Mountain Dew Overdose on 2010-04-20
I created the directory in my home folder, put all three files in it, typed make, and got this...

[EMAIL="tyler@lintmagnet:%7E/.xpad"]```
[/EMAIL][EMAIL="tyler@lintmagnet:%7E/.xpad"]tyler@lintmagnet:~/.xpad[/EMAIL]360$ make
make modules -C /lib/modules/2.6.31-21-generic/build SUBDIRS=/home/tyler/.xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-21-generic'
  CC [M]  /home/tyler/.xpad360/xpad.o
/home/tyler/.xpad360/xpad.c: In function ‘xpad_wireless_connect’:
/home/tyler/.xpad360/xpad.c:293: error: implicit declaration of function ‘info’
/home/tyler/.xpad360/xpad.c: In function ‘xpad_open’:
/home/tyler/.xpad360/xpad.c:384: error: ‘struct input_dev’ has no member named ‘private’
/home/tyler/.xpad360/xpad.c: In function ‘xpad_close’:
/home/tyler/.xpad360/xpad.c:410: error: ‘struct input_dev’ has no member named ‘private’
/home/tyler/.xpad360/xpad.c: In function ‘xpad_probe’:
/home/tyler/.xpad360/xpad.c:498: error: ‘struct input_dev’ has no member named ‘cdev’
/home/tyler/.xpad360/xpad.c:499: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/tyler/.xpad360/xpad.o] Error 1
make[1]: *** [_module_/home/tyler/.xpad360] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-21-generic'
make: *** [all] Error 2
```

Any help is much appreciated :(

---

### Post by nvsbl on 2010-06-18
> **Mountain Dew Overdose said:**
> I created the directory in my home folder, put all three files in it, typed make, and got this...

[EMAIL="tyler@lintmagnet:%7E/.xpad"]```
[/EMAIL][EMAIL="tyler@lintmagnet:%7E/.xpad"]tyler@lintmagnet:~/.xpad[/EMAIL]360$ make
make modules -C /lib/modules/2.6.31-21-generic/build SUBDIRS=/home/tyler/.xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-21-generic'
  CC [M]  /home/tyler/.xpad360/xpad.o
/home/tyler/.xpad360/xpad.c: In function ‘xpad_wireless_connect’:
/home/tyler/.xpad360/xpad.c:293: error: implicit declaration of function ‘info’
/home/tyler/.xpad360/xpad.c: In function ‘xpad_open’:
/home/tyler/.xpad360/xpad.c:384: error: ‘struct input_dev’ has no member named ‘private’
/home/tyler/.xpad360/xpad.c: In function ‘xpad_close’:
/home/tyler/.xpad360/xpad.c:410: error: ‘struct input_dev’ has no member named ‘private’
/home/tyler/.xpad360/xpad.c: In function ‘xpad_probe’:
/home/tyler/.xpad360/xpad.c:498: error: ‘struct input_dev’ has no member named ‘cdev’
/home/tyler/.xpad360/xpad.c:499: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/tyler/.xpad360/xpad.o] Error 1
make[1]: *** [_module_/home/tyler/.xpad360] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-21-generic'
make: *** [all] Error 2
```

Any help is much appreciated :(

Someone named 'Lurch' on the Google Group associated with this code has amended the code to fix this error. Replace the xpad.c file you have with this one, and delete your xpad.h file.

Then just

make
sudo make install

And only add xpad to /etc/modules. Reboot, run jscalibrator to confirm it worked, then open FoF.

---

### Post by mizziga on 2011-11-21
Hello, it's been sometime since the last post and I was hoping to get the guitar work with oneiric. I tried the makefile linked in the referred page and the latest xpad.c published here. but I'm getting the following error msg.
Can anyone help? Thanks!!!


[I]mizziga@mizzigat:~/Downloads$ make
make modules -C /lib/modules/3.0.0-12-generic/build SUBDIRS=/home/mizziga/Downloads
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /home/mizziga/Downloads/xpad.o
/home/mizziga/Downloads/xpad.c: In function ‘xpad_init_output’:
/home/mizziga/Downloads/xpad.c:506:2: error: implicit declaration of function ‘usb_buffer_alloc’ [-Werror=implicit-function-declaration]
/home/mizziga/Downloads/xpad.c:506:14: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/mizziga/Downloads/xpad.c:527:2: error: implicit declaration of function ‘usb_buffer_free’ [-Werror=implicit-function-declaration]
/home/mizziga/Downloads/xpad.c: In function ‘xpad_probe’:
/home/mizziga/Downloads/xpad.c:740:14: warning: assignment makes pointer from integer without a cast [enabled by default]
cc1: some warnings being treated as errors

make[2]: *** [/home/mizziga/Downloads/xpad.o] Error 1
make[1]: *** [_module_/home/mizziga/Downloads] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [all] Error 2[/I]

---

### Post by Perfect Storm on 2011-11-21
Please start a new thread, this one is nearly 4 years old.


Thread closed.

---

