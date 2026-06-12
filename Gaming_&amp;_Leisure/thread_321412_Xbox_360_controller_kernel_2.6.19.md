---
title: "Xbox 360 controller kernel 2.6.19"
date: 2006-12-18
forum: Gaming &amp; Leisure
---

### Post by Horbert on 2006-12-18
I am using xubuntu with an upgrade kernel to 2.6.19 attempting to get an official wired Xbox 360 controller to work.  

I am following these two sets of instructions:
[http://ubuntuforums.org/showthread.php?t=164040&highlight=xbox+controller](http://ubuntuforums.org/showthread.php?t=164040&highlight=xbox+controller)
[http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux](http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux)

The xpad.c driver was changed in 2.6.19 to accommodate more DDR usb pads, but was changed significantly from the patch referenced from the gentoo-wiki.

Just downloading the xpad.c and xpad.h files from xbox-linux.cvs.sourceforge and compiling the kernel via the instructions gives me the following error:

drivers/usb/input/xpad.c:54:26: error: linux/config.h: No such file or directory
drivers/usb/input/xpad.c: In function ‘xpad_process_packet’:
drivers/usb/input/xpad.c:161: warning: implicit declaration of function ‘input_regs’
drivers/usb/input/xpad.c: In function ‘xpad_probe’:
drivers/usb/input/xpad.c:451: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
make[4]: *** [drivers/usb/input/xpad.o] Error 1
make[3]: *** [drivers/usb/input] Error 2
make[2]: *** [drivers/usb] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.19.1'

So I looked inside the linux/config.h file from the stock xubuntu 2.6.17 kernel and it said "This file is no longer in use and kept only for backward compatibility."  I then just removed the reference to linux/config.h from the xpad.c file and tried again.  I got a little further but ended up with a new error:

Building modules, stage 2.
MODPOST 798 modules
WARNING: "input_regs" [drivers/usb/input/xpad.ko] undefined!
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.19.1'

If I knew a little more of this code I guess what would need to be done is to strip the Xbox 360 specific stuff out of the xbox-linux.cvs.sourceforge xpad.c and place it into the new xpad.c driver that comes with 2.6.19 kernel changing it to work with the updated file.

At this point I am stumped, and not sure what else to try. Does anyone have any ideas or tips to get this to work? Thank you.

---

### Post by po0f on 2006-12-19
Horbert,

Maybe the xbox-linux xpad source got merged with the mainline driver?  Try building the stock xpad driver and see if it works.  I'll look at it later tonight (after downloading 2.6.19 sources).

---

### Post by Horbert on 2006-12-19
Thanks for taking a look.   I did try with the stock xpad.c and it did not seem to work so I tried the patches.  I won't have access to my box for the next day but I will try again when I get back and see if works or see if I can figure more out.

---

### Post by zachstruck on 2007-01-06
I just compiled the xpad.c and xpad.h from SourceForge under 2.6.19-7, and it works just fine.
If you look at the Gentoo How-to that you linked, it tells you to comment out a couple lines in the xpad.c file and change a few other things.
That line 161 has to be commented out, and I think another should be commented out too.  Just follow the Gentoo How-To and recompile and it should work.

---

### Post by goonies on 2007-07-16
I really wish you guys would specify what kind of controller you are using.... Wireless or Wired.

---

### Post by Beren Camlost on 2007-07-16
> **goonies said:**
> I really wish you guys would specify what kind of controller you are using.... Wireless or Wired.

> **Horbert said:**
> ..an official **wired** Xbox 360 controller..

Quoted and edited for your convenience.

---

