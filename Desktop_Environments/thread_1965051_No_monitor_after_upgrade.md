---
title: "No monitor after upgrade"
date: 2012-04-25
forum: Desktop Environments
---

### Post by oygle on 2012-04-25
Hi,

Just about everytime there is a Ubuntu upgrade, I loose the monitor. That is, when there is a Linux upgrade usually.

I do use a KVM switch, hope that is not the problem. It is a viewsonic, 19" monitor, here are the logs

> 
(II) Initializing built-in extension DAMAGE
(II) AIGLX error: dlopen of /usr/lib/dri/nouveau_dri.so failed (/usr/lib/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
(II) AIGLX: reverting to software rendering
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) NOUVEAU(0): Setting screen physical size to 338 x 270
resize called 1280 1024
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0


$ sudo lspci |grep VGA
[sudo] password  
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)

Can you help please.

Should I use 'suggestion 1" or suggestion 2" in [http://ubuntuforums.org/showpost.php?p=10620613&postcount=4](http://ubuntuforums.org/showpost.php?p=10620613&postcount=4)

Or, just simply use "System-->Admin-->Hardware. Selected proprietary driver for Nvidia" ?

Oygle

---

### Post by oygle on 2012-04-30
Hi,

This is still a problem ? Can I boot into a (simple) graphics mode ?

Should I just install the NVIDIA drivers ? That is, what is safest to run ?

---

### Post by DaizNaew on 2012-04-30
Heyo.

I have been running ubuntu 12.04LTS beta on my laptop (packard bell dot s2) for quiet some time now, with barely any problems.
After updating to the release version of 12.04LTS I lost connection to my screen too.
I am currently on the laptop and managed to boot into my second OS (Lubuntu 11.10) which works fine.
Anyone got some advice what to do and why it happens?

---

### Post by oygle on 2012-05-02
If I follow step 1 as follows ..

Suggestion 1: Install the proprietary driver through Ubuntu-X-Swat's PPA, it offers more recent drivers than the offical repos:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-current

```

Make sure that a proper xorg.conf is present:

```

sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate

```

.. will the install of "nvidia-current" from the ppa:ubuntu-x-swat/x-updates handle all the dependencies and any packages 'not needed' in my current config ?  There are quite a few 'nvidia' packages currently, plus xorg and other associated ones.

---

