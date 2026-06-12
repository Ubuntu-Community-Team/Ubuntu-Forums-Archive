---
title: "XDirectFB"
date: 2005-12-24
forum: General Help
---

### Post by wfx on 2005-12-24
Hi,
how do i enable/install XDirectFB?
Link: [http://www.directfb.org](http://www.directfb.org)

I want to use it on my Sony Vaio C1VE.
Ubuntu is installed but Xorg and Gnome is a bit to mutch for this litle device.
So i want to install XDirectFB and XFCE4.

Thanks a lot and happy xmas.

---

### Post by frogger255 on 2008-05-10
I would love to write a how to on the subject.

Unfortunately I've run into a bit of a snag installing the fusion.ko
kernel module.  If somebody could help me out with compiling kernel modules under Ubuntu I could no doubt walk everybody through the other steps.

The following occurs when i try to make the module irrespective of what version of fusion I use:

rm -f linux/drivers/char/fusion/Makefile
ln -s Makefile-2.6 linux/drivers/char/fusion/Makefile
make -C /lib/modules/2.6.24-16-generic/build \
                CPPFLAGS=" -D__KERNEL__ -I`pwd`/linux/include -I/lib/modules/2.6.24-16-generic/build/include -I/lib/modules/2.6.24-16-generic/source/include -include /lib/modules/2.6.24-16-generic/build/include/linux/autoconf.h" \
                SUBDIRS=`pwd`/linux/drivers/char/fusion modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.o
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:24:26: error: linux/fusion.h: No such file or directory
In file included from /usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/fusiondev.h:20,
                 from /usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:26:
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/entries.h:60: error: ‘FUSION_ENTRY_INFO_NAME_LENGTH’ undeclared here (not in a function)
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/entries.h:94: warning: type defaults to ‘int’ in declaration of ‘FusionEntryInfo’
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/entries.h:94: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/entries.h:97: error: expected declaration specifiers or ‘...’ before ‘FusionEntryInfo’
In file included from /usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:27:
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/fusionee.h:37: error: expected declaration specifiers or ‘...’ before ‘FusionEnter’
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/fusionee.h:41: error: expected declaration specifiers or ‘...’ before ‘FusionFork’
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/fusionee.h:46: error: expected declaration specifiers or ‘...’ before ‘FusionID’
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/fusionee.h:47: error: expected declaration specifiers or ‘...’ before ‘FusionMessageType’
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/fusionee.h:70: error: expected declaration specifiers or ‘...’ before ‘FusionID’
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/fusionee.h:77: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fusionee_id’
In file included from /usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:29:
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.h:32: error: expected declaration specifiers or ‘...’ before ‘FusionCallNew’
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.h:36: error: expected declaration specifiers or ‘...’ before ‘FusionCallExecute’
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.h:40: error: expected declaration specifiers or ‘...’ before ‘FusionCallReturn’
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:75: error: expected declaration specifiers or ‘...’ before ‘FusionCallExecute’
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c: In function ‘fusion_call_read_proc’:
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:109: error: implicit declaration of function ‘fusionee_id’
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:109: warning: format ‘%08lx’ expects type ‘long unsigned int’, but argument 3 has type ‘int’
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c: At top level:
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:174: error: expected declaration specifiers or ‘...’ before ‘FusionCallNew’
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c: In function ‘fusion_call_new’:
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:192: error: ‘call_new’ undeclared (first use in this function)
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:192: error: (Each undeclared identifier is reported only once
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:192: error: for each function it appears in.)
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c: At top level:
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:207: error: expected declaration specifiers or ‘...’ before ‘FusionCallExecute’
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c: In function ‘fusion_call_execute’:
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:212: error: ‘FusionCallMessage’ undeclared (first use in this function)
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:212: error: expected ‘;’ before ‘message’
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:213: warning: ISO C90 forbids mixed declarations and code
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:215: error: ‘execute’ undeclared (first use in this function)
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:221: error: ‘FCEF_ONEWAY’ undeclared (first use in this function)
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:222: error: too many arguments to function ‘add_execution’
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:230: error: ‘message’ undeclared (first use in this function)
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:240: error: ‘FMT_CALL’ undeclared (first use in this function)
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:241: warning: passing argument 9 of ‘fusionee_send_message’ makes integer from pointer without a cast
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:241: error: too many arguments to function ‘fusionee_send_message’
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c: At top level:
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:280: error: expected declaration specifiers or ‘...’ before ‘FusionCallReturn’
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c: In function ‘fusion_call_return’:
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:286: error: ‘call_ret’ undeclared (first use in this function)
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c: At top level:
/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.c:444: error: expected declaration specifiers or ‘...’ before ‘FusionCallExecute’
make[2]: *** [/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion/call.o] Error 1
make[1]: *** [_module_/usr/src/linux-fusion-7.0.1/linux/drivers/char/fusion] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [all] Error 2


:mad:

---

### Post by kerry_s on 2008-05-10
what ubuntu version?
if it's the latest xorg->
sudo dpkg-reconfigure xserver-xorg

just go through the setup and select fbdev.

---

### Post by frogger255 on 2008-05-12
Yes, I could do that but I don't really want to run Xwindows nor have I wanted to for some time.

More to the point from the day I first tried Linux to the present day I have had one Kernel Panic, witch was caused by me recompiling the kernel.
Every other problem has been directly related to Xfree86 and then to a lesser extent but still significant Xorg.

I was fortunate in that I understood the difference between the Linux kernel and Xorg / Xfree86.
Most users Don't.

I could go on for hours but the general swing of my argument is that X is a bloated unreliable hunk of cow crap.

The system I would like to be running is as follows:

Gnome
GTK+
DirectFB
Kernel/Framebuffer

I would like XDirectFB for emulation only.

---

### Post by kerry_s on 2008-05-12
look here-> [http://www.directfb.org/wiki/index.php/XDirectFB:About](http://www.directfb.org/wiki/index.php/XDirectFB:About)

it says if there's errors, check the header and makefile is there.

---

### Post by frogger255 on 2008-05-13
I think I found the problem.
Its looking for fusion.h amongst the kernel header files and not finding it.

I checked the current kernel with uname -r

It's 2.6.24-16-generic
The corresponding headers are available in /usr/src
which is where Im building fusion.ko (in its own subdirectory)

Does anybody know why this file might be missing. :confused:

---

