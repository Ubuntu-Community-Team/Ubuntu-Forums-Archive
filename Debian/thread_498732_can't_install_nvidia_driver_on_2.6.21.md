---
title: "can't install nvidia driver on 2.6.21"
date: 2007-07-11
forum: Debian
---

### Post by angryfirelord on 2007-07-11
After upgrading to a 2.6.21 kernel, I found out to my unpleasant surprise that I couldn't get my nvidia drivers to install. The error is the same as this one: [http://www.debianhelp.org/node/8691]("http://www.debianhelp.org/node/8691")
```
LD [M] /usr/src/modules/nvidia-kernel/nv/nvidia.o
Building modules, stage 2.
MODPOST 1 modules
FATAL: modpost: GPL-incompatible module nvidia.ko uses GPL-only symbol 'paravirt_ops'
make[4]: *** [__modpost] Error 1
make[3]: *** [modules] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.21-2-686'
NVIDIA: left KBUILD.
nvidia.ko failed to build!
```
> The problem is that post 2.6.18 Debian kernels have PARAVIRT_CONFIG and
nvidia does not like that.

You can either rebuild the kernel and turn that off (Note: but in that
case I had hard hangs in qemu!) *or* use the descriptions in that page
to rebuild the kbuild .deb and install nvidia so it does not mind paravirt.

You'll hit the problem both with m-a *and* the nvidia installer.


I know if I roll back to a 2.6.18 kernel, that'll fix it, but I want to know if anyone else has the same problem and if a bug report has been submitted.

---

### Post by 5-HT on 2007-07-11
It's known, but as to the .config being changed....
You can always roll your own kernel for >=2.6.21 that will play nice with nvidia by disabling  PARAVIRT_CONFIG.
cheers,

---

### Post by kinematic on 2007-07-23
if you would have looked over at the debian forum you would have found a driver wich uses a modified makefile that allows installation.

---

### Post by andrek on 2007-07-23
Dude I had the same problem.
Download this driver : [http://www.nvidia.com/object/linux_display_ia32_1.0-9639.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9639.html)
Then, unpack it with 
sh NVI* -x
and follow these tips :
> 1. Go to the directory where you have your unpacked driver (the one with nvidia-installer file)
2. cd usr/src/nv/
3. open with your favourite editor Makefile.kbuild and just after line 77 that should read
something like this :

EXTRA_CFLAGS += -Wall -Wimplicit -Wreturn-type....bla bla bla....

add the following two lines:

PARAVIRT_OPS := $(shell grep "D paravirt_ops" /boot/System.map-$(shell uname -r) | colrm 9)
EXTRA_LDFLAGS := --defsym paravirt_ops=0x$(PARAVIRT_OPS)


4. change back to the directory of nvidia-installer ( cd ../../../ ) and run it ( ./nvidia-installer )

---

### Post by angryfirelord on 2007-07-23
> **kinematic said:**
> if you would have looked over at the debian forum you would have found a driver wich uses a modified makefile that allows installation.
I know because I'm the one who made the new thread about it. :) I just never bothered to report back here (oops).

[http://forums.debian.net/viewtopic.php?t=17155&highlight=nvidia]("http://forums.debian.net/viewtopic.php?t=17155&highlight=nvidia")

---

