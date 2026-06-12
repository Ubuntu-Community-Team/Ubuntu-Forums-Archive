---
title: "Mega Drive / Genesis controller on Ubuntu"
date: 2005-09-01
forum: Gaming &amp; Leisure
---

### Post by SirKalten on 2005-09-01
Trying to get my Mega Drive controllers to work with Ubuntu.  My Sega is still fine, but the adapter is shot and I hate fiddling with all my cartridges.  I've got legal copies of the games, and legal ROMs aswell, so there's no issue of that.  Just can't work out how to get it to work?

I've tried
# modprobe joydev
# modprobe db9

but I get greated with FATAL: Error inserting db9: No such device.

Any ideas?

---

### Post by SirKalten on 2005-09-02
*coughs*

And I need to find an emulator that'll support joysticks etc in Linux... o.0

( I have the GENS SF version, but I can't seem to get the controller to run it )

---

### Post by theToolman on 2005-10-03
Make sure the package joystick is installed; then:

You need to specify options when loading the db9 module; the docs say the parameter is db9={0|1},{0-10} but I have found that this parameter is actually named dev={0|1},{0-10} - the first is the /dev/lpx number to use, and the second is the device type; see:

zcat /usr/share/doc/joystick/input/joystick-parport.txt.gz

I havent got this going yet as I am getting:
> 
toolman@dev-toolman:~$ s modprobe -v db9 dev=0,1
insmod /lib/modules/2.6.10-5-686/kernel/drivers/input/joystick/db9.ko dev=0,1
FATAL: Error inserting db9 (/lib/modules/2.6.10-5-686/kernel/drivers/input/joystick/db9.ko): No such device
toolman@dev-toolman:~$ dmesg | tail -n 2
parport0: cannot grant exclusive access for device db9
db9.c: parport busy already - lp.o loaded?
toolman@dev-toolman:~$       

---

### Post by dj_flx on 2006-03-26
Say, did this ever get resolved?

I'm getting the same results. I have zero experience dealing with PC-style game ports and the like (I've always had ADB and USB) so this is new to me.

---

### Post by bobo1on1 on 2006-10-05
I did get my psx dualshock controller to work, it was quite easy.

edit /etc/modules:
sudo nano /etc/modules

Place a # before lp.

Add a new line in the bottom:

gamecon map=0,7

Where 0 is parallel port 0 and 7 is for a psx controller.

Then exit and save by pressing ctrl-x.


This is from gamecon.c:

#define GC_SNES         1
#define GC_NES          2
#define GC_NES4         3
#define GC_MULTI        4
#define GC_MULTI2       5
#define GC_N64          6
#define GC_PSX          7
#define GC_DDR          8
#define GC_SNESMOUSE    9

This is my /etc/modules file:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

#lp
psmouse
sbp2
sr_mod

gamecon map=0,7

```

For a genesis controller instead of using gamecon you should use db9 like this:

db9 dev=0,3

Where 0 is parallel port 0 and 3 is a genesis controller.

This is from db9.c:

#define DB9_MULTI_STICK         0x01
#define DB9_MULTI2_STICK        0x02
#define DB9_GENESIS_PAD         0x03
#define DB9_GENESIS5_PAD        0x05
#define DB9_GENESIS6_PAD        0x06
#define DB9_SATURN_PAD          0x07
#define DB9_MULTI_0802          0x08
#define DB9_MULTI_0802_2        0x09
#define DB9_CD32_PAD            0x0A
#define DB9_SATURN_DPP          0x0B
#define DB9_SATURN_DPP_2        0x0C
#define DB9_MAX_PAD             0x0D


Now you have to reboot, or use some magical command I don't know about :P


When everything works you should have a /dev/input/js? device where ? is a number, since this is my only joystick I have a js0 device.
This is what my /dev/input dir looks like:
```

root@bob:/dev/input# ls
event0  event1  event2  event3  js0  mice  mouse0  ts0

```

You can test the joystick with "sudo cat /dev/input/js0" and press some  buttons on the joystick, you should get some strange characters when you press the buttons, then you know it works.

---

### Post by begemot. on 2008-05-12
OMG!
Thank You, **bobo1on1**!
My Sega Genesis joystick come alive completly!!! (:

**ADD:**
I couldn't realize how joy2key works, but [rejoystick]("http://rejoystick.sourceforge.net/") absolutely solved my problem! It's incredibly simple to use and deb-package is also available.

That's perfect!
Thanks again.

---

### Post by begemot. on 2008-05-14
Aagrh...
Guys, i'm getting greedy now, so i whant to use 2 Sega Genesis joysticks over my LPT-port.
Is it possilble?
In the Kernel documentation there is [info]("http://www.mjmwired.net/kernel/Documentation/input/joystick-parport.txt") about db9 driver saying that it supports only one joystick per one LPT-port, but there are some strange words in section **3.2 db9.c**
> 501 Should you want to use more than one of these joysticks/pads at once, you
502 can use db9.dev2 and db9.dev3 as additional command line parameters for two
503 more joysticks/pads.

So, there IS some way to make 2 joysticks to work with db9 driver?!

---

