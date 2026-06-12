---
title: "ATi Radeon: not working, getting desperate"
date: 2005-05-31
forum: Desktop Environments
---

### Post by Heliode on 2005-05-31
Hey,

I'm trying to get my ATi Radeon 9800 XT working properly with the fglrx drivers, but I can't get the damned thing working for the life of me. 

I've installed the restricted-modules for my kernel
I've installed the xorg-driver-fglrx package
I've edited my /etc/X11/xorg.conf to say 'fglrx' in stead of 'ati'
I've added 'fglrx' to /etc/modules
And I've even rebooted.

In spite of all of that, when I do 'fglrxinfo' I get:
```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

In /var/log/Xorg.0.log I find:

```

(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

I've tried fixes in several howto's, including, but not limited to: 
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)
[http://www.ubuntuforums.org/showthread.php?t=22496](http://www.ubuntuforums.org/showthread.php?t=22496)
[http://www.ubuntuforums.org/showthread.php?t=3567](http://www.ubuntuforums.org/showthread.php?t=3567)
[http://www.ubuntuforums.org/showthread.php?t=32495](http://www.ubuntuforums.org/showthread.php?t=32495)
and
[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)

But I can't get it working no matter what I try :'(
I'm about to throw my keyboard out the window so any help here would be greatly appreciated!!

---

### Post by shakin on 2005-05-31
Have you run fglrxconfig and let that make an XF86Config file for you? Backup xorg.conf, run fglrxconfig, then rename XF86Config to xorg.conf.

---

### Post by allans on 2005-05-31
The one thing that doens't seem to get mentioned, or if it has I've missed it, is that after installing fglrx-kernel-source, you have to go to /usr/src and untar it.  After doing this, I had no problems.  Also, if modifying your existing xorg.conf or running fglrxconfig, my card wouldn't work unless I changed my xorg.conf device section to this:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseInternalAGPGART"	"no"
EndSection

The UseinternalAGPGART option was needed, but I'm not sure if this was just for my particular set up.  Good luck!

---

### Post by Heliode on 2005-05-31
[QUOTE=allans]The one thing that doens't seem to get mentioned, or if it has I've missed it, is that after installing fglrx-kernel-source, you have to go to /usr/src and untar it.  After doing this, I had no problems.  Also, if modifying your existing xorg.conf or running fglrxconfig, my card wouldn't work unless I changed my xorg.conf device section to this:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseInternalAGPGART"	"no"
EndSection

The UseinternalAGPGART option was needed, but I'm not sure if this was just for my particular set up.  Good luck![/QUOTE]

I do have the same info in my modules section, but I haven't tried the unpacking of the fglrx-kernel-source. I found it kind of strange this wasn't mentioned anywhere. What do I do with it after I unpack it? Thanks a lot for your help! Hope is a great thing! ;)

Edit:

Ok, I think i've come to a bit more insight: I have a working driver for my kernel version that resides in /lib/modules/fglrx, called fglrx.2.6.10-5-686-smp.ko. There is also a symlink there called fglrx.ko, pointing to the actual driver. I have some faith that this is indeed the correct driver, as its name implies that it is indeed the correct version for my kernel. Now, the problem seems to be that this driver isn't actually being by the system. 

I've tried removing the old xorg-driver-fglrx that I got from the repositories, but that gave me:

```

dpkg-divert: rename involves overwriting `/usr/X11R6/lib/libGL.so.1.2' with
  different file `/usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa', not allowed

```

And failed. Any other way to make it use the correct driver? 

I think the problem here is that I now have a good kernel module, but the system still (tries to) load the wrong version of it, hence the error in Xorg.0.log.
What I need now is a way to make the thing load the right driver. 

I've tried everything I could think of (including simply replacing the fglrx.ko in my /lib/modules/2.6.10-5-686-smp/kernel/drivers/video dir with the 'correct' one) but somehow that didn't make any difference.)

---

### Post by allans on 2005-06-01
Hmm that does ring a bell, to be honest with you I've found the official hoary drivers totally hit and miss, during development I decided to try the latest drivers from ati's site and install them and file names similar to those were mentioned.  They worked perfectly, other than some slight apt problems.  I haven't found the thread yet but if I do I'll post back here.

Allan

---

### Post by allans on 2005-06-02
Hope this is of use:

1. Download official driver .rpm from the ATI website.
2. Remove fglrx packages using synaptic.
3. Shut down gnome. [ From terminal: sudo /etc/init.d/gdm stop ]
4. cd to where you downloaded the driver rpm file.
5. sudo alien fglrx_6_8_0-8.10.19-1.i386.rpm
6. sudo mv /lib/modules/YOURKERNELVERSIONHERE/kernel/drivers/video/fglrx.ko $HOME
7. dpkg --force-overwrite fglrx_6_8_0-8.10.19-1.i386.deb
8. cd /lib/modules/fglrx/build_mod
9. sudo sh make.sh
10. cd /lib/modules/fglrx
11. sudo sh make_install.sh
12. modprobe fglrx
13. fglrxconfig

credit to delltony.

Unfortunately, I don't have a /lib/modules/fglrx dir, I'm not sure if this is a good sign or not!  If you happen to have a build_mod file in there, this will hopefully work.  If is isn't, and you don't mind using a different driver, I'd try the latest ati driver.

The only problem you'll have is if ubuntu wants to update the x.org server with security updates, it'll complain but won't do any damage.

Allan

---

### Post by Heliode on 2005-06-02
AT LAST! I got it working! I can't thank you enough! You've saved my keyboard!

i'm having an average glxgears score of 4530 now!  :grin: 

Tuxracer and Cedega here I come! ;)

---

### Post by allans on 2005-06-03
No probs, glad you got it working.

Allan

---

