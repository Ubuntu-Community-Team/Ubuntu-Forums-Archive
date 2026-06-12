---
title: "problems Installing fglrx 8.8.25 in warty"
date: 2005-01-18
forum: General Help
---

### Post by Scottles on 2005-01-18
Hi,
I have spent all evening trying to update to the new ATi fglrx 8.8.25 drivers in warty. I downloaded the rpm and used alien to convert it to a deb package, and then proceeded to stop gdm and then install teh package using:
 dpkg --force-overwrite -i fglrx-4-3-0_8.8.25-2_i386.deb

this appeared to install ok, so i then proceeded to build the module doing a:
cd /lib/modules/fglrx/build_mod
sh make.sh
cd /lib/modules/fglrx
sh make_install.sh
modprobe fglrx

I also ran fglrxconfig to ensure settings were correct and then i tried restarting X (/etc/init.d/gdm start). It started fine, but fglrxinfo shows that only the mesa opengl drivers were being used, not the hardware accelerated ones.. i have spent all evening trying to get these new ATi drivers working.. spent a lot of time searching these forums for help.. but no luck so far.. i never had problems like this getting them working in slackware 10.. it was dead easy! Anyone managed to get them working in warty and got any tips?

---

### Post by ante0 on 2005-01-20
is there any new drivers for the 7000 series of ATI Radeon? Can only use the vesa driver... =/

edit: just installed ubuntu and the ati driver worked.
(does anyone know why it doesnt work in vectorlinux??! =) )
//Ante

---

### Post by Exxtreme on 2005-01-22
[QUOTE=Scottles]I also ran fglrxconfig to ensure settings were correct and then i tried restarting X (/etc/init.d/gdm start). It started fine, but fglrxinfo shows that only the mesa opengl drivers were being used, not the hardware accelerated ones.. i have spent all evening trying to get these new ATi drivers working.. spent a lot of time searching these forums for help.. but no luck so far.. i never had problems like this getting them working in slackware 10.. it was dead easy! Anyone managed to get them working in warty and got any tips?[/QUOTE]
I had the same problem but now it works. You have to delete/rename the /lib/modules/<your kernel-version>/kernel/drivers/video/fglrx.ko. Then /lib/modules/<your kernel-version>/kernel/drivers/char/drm/fglrx.ko will be used and this is the right one.

---

### Post by Scottles on 2005-01-23
Cool, thanks... i would have thought apt-get would have removed the original fglrx.ko file when i removed the warty fglrx-driver package... guess not... thanks for the tip :)

---

### Post by Mastodront on 2005-01-25
[QUOTE=Exxtreme]I had the same problem but now it works. You have to delete/rename the /lib/modules/<your kernel-version>/kernel/drivers/video/fglrx.ko. Then /lib/modules/<your kernel-version>/kernel/drivers/char/drm/fglrx.ko will be used and this is the right one.[/QUOTE]


Hmm, this sounds exactly like my problem (another thread I started today). Even though I have installed xorg and xorg-driver-fglrx (seems to work fine now) it uses Mesa instead of hw-accelerated Open GL (around 90 fps in glxgears :P). I tried you tip and removed fglrx.ko and restarted my computer but nothing had changed at all. One thing I noticed was that I didn't have any fglrx.ko in the other folder (*/char/drm/), there were some other *.ko files though, like a radeon.ko.

I have a Radeon 9600XT btw

Any tips?

---

### Post by shakakan on 2005-01-25
I am having the same problems  I have a Radeon 9250 PCI, fglrx is installed, but it is still using MESA GLX for OpenGL.

Running Hoary BTW.

---

### Post by Mastodront on 2005-01-26
[QUOTE=Mastodront]Hmm, this sounds exactly like my problem (another thread I started today). Even though I have installed xorg and xorg-driver-fglrx (seems to work fine now) it uses Mesa instead of hw-accelerated Open GL (around 90 fps in glxgears :P). I tried you tip and removed fglrx.ko and restarted my computer but nothing had changed at all. One thing I noticed was that I didn't have any fglrx.ko in the other folder (*/char/drm/), there were some other *.ko files though, like a radeon.ko.

I have a Radeon 9600XT btw

Any tips?[/QUOTE]

When I remove the file you said it doesn't load any fglrx-module at all

This is the error I get (from Xorg.0.log):

(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 3.12.0
(II) fglrx(0):     Date: Jul 16 2004
(II) fglrx(0):     Desc: ATI Fire GL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0a97000 at 0x4024f000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

It seems like it's using a VERY old fglrx . 

Any suggestions on what to do?

---

