---
title: "ATI driver - No 3D Acceleration!! HELP!!"
date: 2006-01-13
forum: General Help
---

### Post by Mastadex on 2006-01-13
Ive been desperately trying to get 3D acceleration to work in ubuntu for the last few days. I got the ati driver sort of installed. Unfortuantely when I go to the ATI control panel it has a few things wrong:

Transfer Mode: PCI  <----- THis should be AGP, its an AGP card after all
OpenGL drivers: Mesa  <-- These are not being replaced by ATI's version for some reason.

I checked out the Xorg log:

(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work


The kernel module [8.16.20] is not the same as the driver that i installed from ATI's website [8.20.08]. So its not loading.

I tried all those modifications to /etc/X11/xorg.conf, those dont work. 

Can anyone help me with this poblem?

---

### Post by Zimmer on 2006-01-13
Hi
Have a look here, particularly the troubleshooting section which shows the error you are getting.
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

Be careful you do not get in a mess installing one set of drivers over another. Uninstalling and starting agin using the wiki is a good idea.
Make sure you are SURE which drivers you are installing. Personally I use the fglrx drivers , not the ones fronm the ATI site...but each to his own...

---

### Post by Mastadex on 2006-01-13
I would like to know where you got your fglrx drivers and if they are any better then the ones from ATI's site?

---

### Post by Greg2 on 2006-01-13
I didn’t have much luck with the 8.16.20 drivers. So I followed this HowTo for the latest ATI fglrx version:
[http://ubuntuforums.org/showthread.php?p=423589&posted=1#post423589](http://ubuntuforums.org/showthread.php?p=423589&posted=1#post423589)

If you follow the instructions you will have no problems... and you will be very pleased with the results.:smile:

---

### Post by Mastadex on 2006-01-13
I followed that website posting to the letter. every command was successful. and now im back. 3D acceleration does not work, and the ATI control panel now does not show the driver information.

Here is my kern.log snip:
Jan 13 21:33:10 localhost kernel: [4294686.374000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Jan 13 21:33:10 localhost kernel: [4294686.377000] [fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
Jan 13 21:33:10 localhost kernel: [4294686.377000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Jan 13 21:33:10 localhost kernel: [4294686.377000] [fglrx] module loaded - fglrx 8.20.8 [Dec  6 2005] on minor 0
Jan 13 21:33:10 localhost kernel: [4294686.406000] [fglrx] ACPI power management is initialized.

Also, i did a glxinfo, and it still displays the mesa drivers for openGL.

I am stumped.

---

### Post by newuser111 on 2006-01-13
have you tried sudo fglrxconfig in a terminal

you can just press enter to most answers it asks

---

### Post by Mastadex on 2006-01-13
ofcourse, its the first thing i tried.

Also, I traked down an older vewsion of the FireGL driver - fglrx 8.16.20 - and it appears to load ok, without any problems. Although here is another problem, and its possibly the root of my headache: 

[Xorg.0.log]

(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EINVAL"
(EE) fglrx(0): cannot init AGP

Its having trouble initializing the AGP. I have no idea why, and i think i say this in the newer driver aswell, although i cannot remember the exact line.

**[Edit 2]**
Here is the complete listing of the Log where errors and warnings appear:
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Loading extension MIT-SCREEN-SAVER
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EINVAL"
(EE) fglrx(0): cannot init AGP
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


Also i just did an dmesg and found some lines that might be a bit of use:

[4294733.516000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[4294733.516000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294733.516000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294733.516000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294733.516000] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[4294733.517000] [fglrx:firegl_unlock] *ERROR* Process 7491 using kernel context 0

---

### Post by Zimmer on 2006-01-13
[QUOTE=Mastadex]I would like to know where you got your fglrx drivers and if they are any better then the ones from ATI's site?[/QUOTE]
I followed the wiki instructions that I posted earlier to install the 8.16.20 fglrx drivers.
They work for me...Radeon 9600 card...
You have already tried installing the ATI 8.20.8  drivers from the ATI site from the look of that log.
So, either the xorg.conf file needs some adjustment or the drivers have not been installed correctly. Check the device section of xorg.conf  says Driver "fglrx" is a good start.
I am not expert enough to tell you definitively how to exactly recover the situation and start again. When I had problems with Ubuntu 5.04 and graphics cards when I first started, I was swapping ATI and NVidia cards from one computer to another..and re installing Ubuntu from scratch each time to get the GUI back !! I then followed the wiki instructions (carefully, reading to the bottom before starting ) for the fglrx drivers that come with Ubuntu, not the ones from the ATI site.
ALso, this note form the wiki may have some bearing on your original situation with the 8.16.20 drivers:

Note If you are having problems related to DRI or 3d acceleration and the following lines show up in your /var/log/Xorg.0.log

(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work

then make sure you have linux-restricted-modules installed for your kernel (type sudo apt-get install linux-restricted-modules-$(uname -r)). 

....
Regards(I must sleep it's 3:20 am here!)

---

### Post by Mastadex on 2006-01-13
i did a cat xorg.conf | grep "fglrx" and found the driver is actually fglrx and not ati.

I also do have the latest version of the restricted files.

---

### Post by flight_master on 2006-01-14
Mastadex,

Have a look at [HowTo: ATI fglrx Hardware Acceleration](http://ubuntuforums.org/showthread.php?t=115104&highlight=fglrx+mtrr)

Regards,
Christian

---

