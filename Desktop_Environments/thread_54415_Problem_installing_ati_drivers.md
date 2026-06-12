---
title: "Problem installing ati drivers"
date: 2005-08-04
forum: Desktop Environments
---

### Post by zeuz on 2005-08-04
I know i have another active thread, but i didn't want to mix them. I tried following theese guides to install the drivers:
[http://www.ubuntuforums.org/showthread.php?t=24557&highlight=ati](http://www.ubuntuforums.org/showthread.php?t=24557&highlight=ati)
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

It's probably something i've missed...  ](*,) 

Some output...

fglrxinfo:
> display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)


/var/log/messages:
> ... kernel: [fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
 

/var/log/Xorg.0.log:
> (EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENOMEM"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0c00000 at 0xb7db4000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


/etc/modules:
> ...
fglrx
 ]

---

### Post by johannes on 2005-08-04
I'm not an expert but I think you need to remove the Mesa drivers before installing the fglrx ones. Otherwise they might mix up somehow, which I believe is your case. If you installed Mesa using synaptic remove them and run the fglrx install again.

What hardware do you use?

---

### Post by zeuz on 2005-08-05
Oops, didn't even think of that. I'll try when i get home from work, thanks. :) I have an nforce2 motherboard (asus a7n8x deluxe) and 9500 pro.

---

### Post by zeuz on 2005-08-05
When i check mesa to be removed synaptic wants to remove _alot_ of other packages, any other way to solve it?

---

### Post by zeuz on 2005-08-06
Still hasn't figured out to solve this. :(

Another problem, can't play .mov with either mplayer or vlc. I have installed theese codecs: [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

---

### Post by mgorbach on 2005-08-06
[QUOTE=zeuz]Still hasn't figured out to solve this. :(

Another problem, can't play .mov with either mplayer or vlc. I have installed theese codecs: [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)[/QUOTE]
 zeuz what are you getting when you install flrx drivers?
black screen?
if so we have the same probelm ... iv got nforce3 chipset as well and ati x800xt.
Lets try to solve it together.

---

### Post by johannes on 2005-08-06
Can you post your /etc/X11/xorg.conf?

---

### Post by zeuz on 2005-08-06
[QUOTE=mgorbach]zeuz what are you getting when you install flrx drivers?
black screen?
if so we have the same probelm ... iv got nforce3 chipset as well and ati x800xt.
Lets try to solve it together.[/QUOTE]

No black screen/error messages. :(

[QUOTE=johannes]Can you post your /etc/X11/xorg.conf?[/QUOTE]

Attached it. :)

---

### Post by zeuz on 2005-08-08
Have a third problem now. Maybe not ubuntu specific, but someone here may be able to help me. 

I recently moved and took my server with me. I had dsl where i lived before and now i have cable which uses dhcp. My current dist on the server is gentoo. Tried to get it online with dhcpcd but it didn't work. Tried to use the ubuntu installation. It found both of the cards but i couldn't get it to work with dhcp. The cable works fine on this machine, both in windows and ubuntu. Any ideas?

---

### Post by johannes on 2005-08-09
I assume you have installed the linux-headers-2.6.10-5? (or whatever kernel you're using.)

Well, I can't see anyting wrong from the information you have posted, so the problem probably lies somewhere else. I think you should try installing the latest drivers from ATI's website following this howto: [http://www.ubuntuforums.org/showthread.php?t=32495&highlight=radeon](http://www.ubuntuforums.org/showthread.php?t=32495&highlight=radeon) (remember to backup your /etc/X11/xorg.conf)

If it doesn't work and you can't log into X, backup your new /etc/X11/xorg.conf, change back to the old one and follow this: [http://www.ubuntuforums.org/showpost.php?p=206829&postcount=87](http://www.ubuntuforums.org/showpost.php?p=206829&postcount=87), then change back to the newest.

---

### Post by zeuz on 2005-08-09
The installation went fine, but it still wont work. I didn't remove the synaptic drivers, should i have done that?  ](*,) 

Kernel: 2.6.10-5-386
Linux-kernel-headers: 2.5.999-test7-bk-17

I have linux-restricted-modules-2.6.10-5-386 installed.

I don't have build-essentials installed, but there were no errors during the installation?

Some lines from /var/log/Xorg.0.log:
> (II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.8.25
(II) fglrx(0):     Date: Jan 14 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0c0a000 at 0xb7dae000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

The only thing i have in /lib/modules/fglrx is:
> drwxr-xr-x  3 root root  4096 2005-08-09 18:59 build_mod
-rwxr-xr-x  1 root root 10157 2005-08-09 18:59 make_install.sh

---

### Post by johannes on 2005-08-09
There is a difference between "linux-restricted-modules-2.6.10-5-386", "Linux-kernel-headers: 2.5.999-test7-bk-17" and "linux-headers-2.6.10-5-386". You should install the latter ("linux-headers-2.6.10-5-386").

If it doesn't work automatically, run /lib/modules/fglrx/make_install.sh, then copy the  fglrx.ko and fglrx.2.6.10-5-386.ko as mentioned in [http://www.ubuntuforums.org/showpost.php?p=206829&postcount=87](http://www.ubuntuforums.org/showpost.php?p=206829&postcount=87).

---

### Post by zeuz on 2005-08-09
Thanks for all the help you've given me. :) There are still some problems though...

When i rebooted and checked "ATI Control", it said I used the new drivers. Tried to start enemy-territory and the screen got black. Restarted X and checked ATI Control again. MESA! ...

/var/log/Xorg.0.log
> (II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.14.13
(II) fglrx(0):     Date: Jun  8 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.10-5-386
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xeb000000
(EE) fglrx(0): Failed to initialize UMM driver.
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0c01000 at 0xb7dae000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

Edit:

Rebooted again and it "works":
[http://img110.imageshack.us/my.php?image=driver0cj.png](http://img110.imageshack.us/my.php?image=driver0cj.png)

fglrxinfo:
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9500 Pro Generic
OpenGL version string: 1.3.5140 (X4.3.0-8.14.13)

fgl_glxgears works.

It's when i start enemy territory it crashes.

Edit2: 

[SIZE=5]IT WORKS![/SIZE]

Rebooted a second time and et works too! Thank you!  \\:D/

---

### Post by johannes on 2005-08-09
:grin: I'm glad I was able to help you.

---

