---
title: "EMS Topgun Driver Module Install"
date: 2007-08-13
forum: Gaming &amp; Leisure
---

### Post by tarotking on 2007-08-13
Hey everyone. 

I'm having a hard time searching for and finding the information that I am looking for. I have been using linux for a while, but have never needed to compile kernel modules myself.

I recently bought a EMS LCD TopGun that I would like to connect to my linux system. I have also acquired the source code to the linux driver. I do not know how to compile, or install the driver to get the device to work.

It came with a Makefile, which does not work for me. I am using Ubuntu 7.04 I believe, Dapper Drake. Linux 2.6.20-16-generic #2 SMP i686 GNU/Linux.

the contents of the makefile are

==============MakeFile=================
TOPDIR          := /usr/src/linux
MOD_ROOT        :=
PWD             := $(shell pwd)

obj-m           := lcdtopgun.o

default:
        $(MAKE) -C $(TOPDIR) SUBDIRS=$(PWD) modules

clean:
        rm -f *.o

install:
        $(MAKE) -C $(TOPDIR) SUBDIRS=$(PWD) modules_install
        depmod -ae
=====================================

the error i get is 

make -C /usr/src/linux SUBDIRS=/home/loudet/Desktop/topgun-0.1 modules
make: *** /usr/src/linux: No such file or directory.  Stop.
make: *** [default] Error 2


Since I have no experience tinkering with the kernel, or compiling modules i didnt want to change information in the makefile without understanding what it wanted to do. My questions are

- what do I need to do under Dapper Drake to compile a driver from source code ?

- What libraries /headers do i need to link to?

- after the module is compiled, where do I need to place the module.

i am sure i can find information about using modprobe to load the driver, but if there is any  other extra information or a reference to a manual i missed, i would appreciate it.

the headers that the source file tries to include are 

==========Includes==============
#include <linux/kernel.h>
#include <linux/slab.h>
#include <linux/input.h>
#include <linux/module.h>
#include <linux/init.h>
#include <linux/usb.h>
=============================

looks like linux is going to make me learn something new again =P

thanks

---

### Post by arfink on 2007-12-02
Hey, I am looking into getting an LCD Topgun as well. I found that the website which had those drivers has gone down, could you email me that file? PM me, I'll give you my email address so you can send it to me. I'll experiment with it, I have Gutsy. (7.10)

Sweet, it's nice to see that someone in the world besides me wants to use this gun with linux.

---

### Post by arbrandes on 2008-03-27
I'm one of the 3 people in the world who wants to use the gun on Linux.  Can't find the driver, though (topgun-0.1.tar.gz, I believe it was called).  Can any of you guys attach it here?

The gun's still in the mail, so I haven't tried using it as a standard USB HID device.

Has anybody has any luck either way?

---

### Post by arfink on 2008-03-27
Hey, welcome to out little and exclusive club!

Actually, I will need to check on where I put those drivers. I never got a response from anyone (as you can tell) so I didn't buy the gun. :(  I don't have Windoze, which is probably the only other easy way to use the gun.

The files USED to be hosted on Kaillera, can't find the there now. I'll check around my HDD and see if I still have them. 

However, there is still hope- the TopGun is actually Guncon2 compatible. See this thread 

[http://forum.arcadecontrols.com/index.php?topic=60813](http://forum.arcadecontrols.com/index.php?topic=60813)

at the BYOAC (build your own arcade controls) website: it might prove to be very helpful, especially since those Guncon2 drivers are much more tested, more is known about them, and they also are updated sometimes. Basicly the TopGun drivers took the Guncon2 ones, and simplified them by adding the hardcoded X,Y, etc. values, which are also posted on that post.

I guess that's all I got for now, let me know how it goes! Be on the lookout for Guncon2 drivers- they are what you are really looking for.

---

### Post by arbrandes on 2008-03-28
Yeah, I already downloaded the guncon2 drivers (although they're still at 0.1).  I'm going to attach them here just in case anybody needs them and the site goes down.

But it stands to reason that Christophe Thibault had some kind of motive to write a especific Linux driver.  I just don't know which one, yet.  So I tried emailing him, let's see if it helps!

Here's to hoping it'll all work out.  My wife something of a light gun addict, and I'm hoping to score some points with Mame (and maybe House of the Dead under wine). :)

[edit]
Too bad the Wayback Machine doesn't store tarballs!
[http://web.archive.org/web/20070118173747/http://kaillera.com/topgun/](http://web.archive.org/web/20070118173747/http://kaillera.com/topgun/)
[/edit]

---

### Post by arfink on 2008-03-28
That's great! I hope things work well for you. If the community got some good drivers maybe we'd also get some open source lightgun games. :) I'm using FreeBASIC, and learning how to integrate with SDL, so I might take a whack at a game if I can get some drivers.

EDIT: OH MY GOSH! I tried the Kaillera site and... it's all there again!! I don't know how that happened! I got the files, you should try and dwonload them now. If it won't work, I can email them to you, or maybe post them up if i can figure out how.

---

### Post by arbrandes on 2008-03-29
Waddya know, it IS back up!  Here's the driver in case the site goes down again.

---

### Post by arfink on 2008-03-30
Well, have you tried to compile the drivers yet? I don't have a clue- and I don't have my gun yet either. I know how to MAKE them, but what do I need to have? Do I need kernel headers? Kern source? What can I do with it once I do compile it? Does it then make the gun work/act like a mouse, or a joystick, or something?

I should email the guy who made the drivers and find out.

---

### Post by arbrandes on 2008-03-31
Bad news: the driver doesn't compile with Gutsy's kernel (or newer ones)l.  My gun hasn't arrived yet, but if it doesn't work as a standard HID device, I'm going to have a go at making the driver work.

And to answer your question, yes, you would need the kernel headers at the very least.  I'll know more when and if I get the driver working.

---

### Post by arbrandes on 2008-03-31
And to answer your other question, by reading the topgun driver I infer it presents itself as a joystick:

```

        /* stick */
	input_report_abs(dev, ABS_X,     gun);
	input_report_abs(dev, ABS_Y,     data[4]);

	/* digital pad */
	input_report_abs(dev, ABS_HAT0X, x);
	input_report_abs(dev, ABS_HAT0Y, y);

```

---

### Post by arbrandes on 2008-04-14
If anybody's still watching the thread, I modified Chris's driver enough that it'll compile and load cleanly in Ubuntu Gutsy.  It wasn't exactly rocket science, but it took a few hours of reading and comparing it to working drivers such as the xpad360.

Oh, and it seems to work!  The gun is recognized as a standard joystick with X and Y axes plus a POV hat, all of which seemed to do fine in my 5-minute test.

I just haven't gotten the buttons and trigger to be recognized yet, and there seems to be some sort of calibration issue.

Will report on further progress as it happens.

---

### Post by arbrandes on 2008-04-14
Buttons done and tested, now to fix calibration.

---

### Post by arbrandes on 2008-04-14
Here it is.  It should work on all kernels up to 2.6.24, including Hardy.

To compile, you will need to have kernel headers installed, but nothing else.  If you do, a "make" followed by "make install" should do the job.  Then, if you plug the topgun in, by running a "jstest /dev/input/js0" you should be able to see if all is well.

You will need to do hardware calibration for it to work.  Follow these instructions (no, you don't need to do it on Windows first):

```

* Point the gun offscreen (the floor/ceiling). Hold down the A and B button at
the same time to enter calibration mode. (you see the laser turn on)
* If Installing 'vertical' LED stands, Shoot the top-left LED group.
* If Installing 'horizontal' LED stands, Shoot the top-right LED group.
* Shoot the following in this order:
    * Center of the screen
    * Top left corner of your screen
    * Top right corner of your screen
    * Bottom right corner of your screen
    * Bottom left corner of your screen 

```

(From: [http://wiki.arcadecontrols.com/wiki/LCDTopGun#Hardware_calibration](http://wiki.arcadecontrols.com/wiki/LCDTopGun#Hardware_calibration))

I still haven't tried playing any games, though.  Suggestions?

---

### Post by arfink on 2008-04-15
Sa-weet! I am so going to try this out. As for games, I would suggest the House of the Dead series, which I have successfully gotten to run in Wine before and which I think can handle joystick inputs. Also another good game that I used to play a ton is Wetlands, which was fun with a joystick and would be even more fun with a gun! I think you could run it with QEMU or DosBox. 

Also give some emulators a shot. I know that emulation is frowned upon in some open source circles, so i won't get into great detail, but I know there are a ton of great lightgun games for MAME, SNES, Playstation, NES, etc. For specific games I would suggest Point Blank, (always fun) Area 51, Duck Hunt, Elemental Gearbolt, (unique and awesome) Lethal Enforcers, Police Trainer, and of course all the House of the Dead and Time Crisis games. With most emulators (except MAME) dumping your own ROMS is not too hard, I have done it on occasion in the past. Of course I cannot and will not tell you to break the law.

Finally, if you have the mad skillz to make this driver I'm sure you could find a neat way to build a game to use them. I am just learning Free Basic and once I get joystick input down I'll start experimenting. 

Thanks for the drivers and keep up the good work!

---

### Post by arbrandes on 2008-04-16
House of the Dead under wine, good idea.  I'm acquiring Time Crisis as we speak.  Oh, and Duck Hunt is already great fun under mame! I'm also curious as to whether I'll be able to emulate PS2 shooters with the Topgun.  That would be decidely awesome!

Hmm, make my own lightgun game?  That would be a lot of fun.  :)

---

### Post by qgranfor on 2008-12-27
Thanks for posting this!  Been trying to get it working right for several hours now.  Looks like a possible calibration issue on my end.......but I've tried both vert and horiz setups.....and still the same issue.

When I issue "jstest /dev/input/js0" the numbers jump around a bit

Event: type 2, time 1409576, number 1, value -9558
Event: type 2, time 1409592, number 0, value 5888
Event: type 2, time 1409592, number 1, value 16383
Event: type 2, time 1409612, number 0, value 17920
Event: type 2, time 1409612, number 1, value 26965
Event: type 2, time 1409636, number 0, value 19584
Event: type 2, time 1409636, number 1, value 28330
Event: type 2, time 1409652, number 0, value 15360
Event: type 2, time 1409652, number 1, value 24575
Event: type 2, time 1409668, number 0, value 17920
Event: type 2, time 1409668, number 1, value 26965
Event: type 2, time 1409724, number 0, value 20352
Event: type 2, time 1409724, number 1, value 29013
Event: type 2, time 1409740, number 0, value 21504
Event: type 2, time 1409740, number 1, value 30378
Event: type 2, time 1409764, number 0, value 19840
Event: type 2, time 1409764, number 1, value 29013
Event: type 2, time 1409780, number 0, value 19712
Event: type 2, time 1409796, number 0, value 17920
Event: type 2, time 1409796, number 1, value 28330
Event: type 2, time 1409804, number 0, value -32767
Event: type 2, time 1409804, number 1, value -32767
Event: type 2, time 1409836, number 0, value 23296
Event: type 2, time 1409836, number 1, value 32426
Event: type 2, time 1409852, number 0, value 23552
Event: type 2, time 1409852, number 1, value 32767
Event: type 2, time 1409876, number 0, value 24192
Event: type 2, time 1409892, number 0, value 25216
Event: type 2, time 1409908, number 0, value 24448
Event: type 2, time 1409924, number 0, value 25472
Event: type 2, time 1409948, number 0, value 26624
Event: type 2, time 1409956, number 0, value -32767
Event: type 2, time 1409956, number 1, value -32767

See how number 1 can be 32767 then -32767 as the next value?

Although, come to think of it......anyone use this code in a 64-bit environment?  Hardy 8.04 AMD64 2.6.24-22  :confused:

---

### Post by NachoSama on 2010-03-01
- Ubuntu 9.10 64b
- Linux 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

Tried to compile the module but it get's me this:
```

make -C /usr/src/linux SUBDIRS=/mnt/sto/home/media/Descargas/topgun.oficial/topgun-0.2 modules
make[1]: se ingresa al directorio `/usr/src/linux-source-2.6.31'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.31/Module.symvers
           is missing; modules will have no dependencies and modversions.

CC [M]  /mnt/sto/home/media/Descargas/topgun.oficial/topgun-0.2/lcdtopgun.o
/mnt/sto/home/media/Descargas/topgun.oficial/topgun-0.2/lcdtopgun.c: In function ‘usb_topgun_open’:
/mnt/sto/home/media/Descargas/topgun.oficial/topgun-0.2/lcdtopgun.c:170: error: ‘struct input_dev’ has no member named ‘private’
/mnt/sto/home/media/Descargas/topgun.oficial/topgun-0.2/lcdtopgun.c: In function ‘usb_topgun_close’:
/mnt/sto/home/media/Descargas/topgun.oficial/topgun-0.2/lcdtopgun.c:188: error: ‘struct input_dev’ has no member named ‘private’
/mnt/sto/home/media/Descargas/topgun.oficial/topgun-0.2/lcdtopgun.c: In function ‘usb_topgun_probe’:
/mnt/sto/home/media/Descargas/topgun.oficial/topgun-0.2/lcdtopgun.c:267: error: ‘struct input_dev’ has no member named ‘cdev’
/mnt/sto/home/media/Descargas/topgun.oficial/topgun-0.2/lcdtopgun.c:268: error: ‘struct input_dev’ has no member named ‘private’
/mnt/sto/home/media/Descargas/topgun.oficial/topgun-0.2/lcdtopgun.c: In function ‘usb_topgun_init’:
/mnt/sto/home/media/Descargas/topgun.oficial/topgun-0.2/lcdtopgun.c:335: error: implicit declaration of function ‘info’
make[2]: *** [/mnt/sto/home/media/Descargas/topgun.oficial/topgun-0.2/lcdtopgun.o] Error 1
make[1]: *** [_module_/mnt/sto/home/media/Descargas/topgun.oficial/topgun-0.2] Error 2
make[1]: se sale del directorio `/usr/src/linux-source-2.6.31'
make: *** [default] Error 2
```

I was searching but have only found a french post in a french ubuntu forum without answer yet.

Thank you all. :)

---

