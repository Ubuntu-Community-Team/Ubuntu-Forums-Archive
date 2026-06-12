---
title: "ATI Proprietary causing video issues."
date: 2011-11-08
forum: Desktop Environments
---

### Post by doxramos on 2011-11-08
I am running on Ubuntu 10.04 (My desktop and 11.10 disagree.) I installed the proprietary drivers 
Description
```

ATI/AMD proprietary FGLRX graphics driver
Tested by the Ubuntu Developers
License: Proprietary
Description:
3D-accelerated proprietary graphics driver for ATI cards.

This driver is required to fully utilise the 3D potential of some ATI graphics cards, as well as provide 2D acceleration of newer cards

```I installed through System-->Administration-->Hardware Drivers and expected it to work, but instead it threw my PC into a state of panic where my entire screen would have lines running all over to the point where you couldn't read anything. If anyone knows what this issue is please give me a hand. My card works without the driver however for the 20 seconds that the prop was working I didn't have to use opengl for games at all. All directx apps were running smooth. Thanks in advance.

lspci output:
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:07.0 Network controller: Broadcom Corporation BCM43XG (rev 01)
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```If you need more information on the system just let me know. (and please tell me how to do it too since I'm not a linux pro by any means. :) )

---

### Post by typhoon_tip on 2011-11-09
You should give a try to the ATI Driver from their site, I think the repo driver in 10.04 is very old (didn't work at all too on my Lenovo T400 with Radeon HD 3400 card).

Follow these **exact steps** to get rid of the repo driver and install the new one:

```
$ sudo sh /usr/share/ati/fglrx-uninstall.sh
$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
$ sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
$ sudo apt-get install xserver-xorg-video-ati
$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

At this point restart, it should be back with stock open source ATI driver and no any 2D acceleration. After restart, do:

```
$ sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0
$ cd ~/; mkdir catalyst11.10; cd catalyst11.10/
$ wget http://www2.ati.com/drivers/linux/ati-driver-installer-11-10-x86.x86_64.run
$ sudo sh ati-driver-installer-11-10-x86.x86_64.run --buildpkg Ubuntu/lucid
$ sudo dpkg -i fglrx*.deb
$ sudo aticonfig --initial -f
```

Beware of the output of aticonfig. If it says command not found or other errors, come back to this thread.

---

### Post by doxramos on 2011-11-09
```


sudo: aticonfig: command not found
name@name-desktop:~/catalyst11.10$ sudo aticonfig
sudo: aticonfig: command not found

```
I'm here with the issue you expected lol. Everything else was going great and I thought I may be in the clear too.

---

### Post by typhoon_tip on 2011-11-09
> **doxramos said:**
> ```


sudo: aticonfig: command not found
name@name-desktop:~/catalyst11.10$ sudo aticonfig
sudo: aticonfig: command not found

```
I'm here with the issue you expected lol. Everything else was going great and I thought I may be in the clear too.

Loll no worries.

First, try this command and see if the output is still something set to MESA:
```
$ update-alternatives --get-selections | grep gl_conf
```

If yes, force the thing to be set into manual like this:
```
$ sudo update-alternatives --set gl_conf /usr/lib/fglrx/ld.so.conf
```

Command "aticonfig" should then work straight away. Remember to use it as "sudo aticonfig --initial -f".

---

### Post by doxramos on 2011-11-10
```


~$ update-alternatives --get-selections | grep gl_conf
gl_conf                        manual   /usr/lib/fglrx/ld.so.conf

```

This is my new output, but when I restarted it had said that the settings were low and stopped working.
Does that mean I screwed up somewhere? lol

---

### Post by doxramos on 2011-11-10
```

There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No AMD graphics driver is installed, or the AMD driver is not functioning properly.
Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.

```

Well that makes me sad. *Sad face goes here.* I followed the directions to the T and not sure what I did wrong. =/

---

### Post by doxramos on 2011-11-10
Okay, so I have a .run file from ATI for the driver that I want to give a try, but one issue. I don't know how to uninstall this driver now that I've done it =/. Linux newbie like I said, and just trying to get everything running up to par. Thanks for the help. :)

---

### Post by typhoon_tip on 2011-11-10
> **doxramos said:**
> Okay, so I have a .run file from ATI for the driver that I want to give a try, but one issue. I don't know how to uninstall this driver now that I've done it =/. Linux newbie like I said, and just trying to get everything running up to par. Thanks for the help. :)

Here to help, passed countless hours on that thing !

First of all, try simply to reinstall all the debians over with the new gconf setting.

Open a terminal and enter the folder where you have created the debians the first time, then:
```
$ sudo dpkg -i fglrx*.deb
$ sudo aticonfig --initial -f
```

It should work straight away this time, let me know. Eventually we try a full purge and reinstall.

:popcorn:

---

### Post by doxramos on 2011-11-10
Well it's working =/ Kind of. It's doing the same thing the prop drivers were doing. Attached a screenshot of the issue.

---

### Post by doxramos on 2011-11-11
Well I feel like a tool. you can't even see it...

---

### Post by typhoon_tip on 2011-11-11
So the lines are not appearing when you do a screenshot, correct ?

What is the Gnome version of Mint 10.04 ? 2.x or 3.2 ? I am not so familiar with Mint...

---

### Post by doxramos on 2011-11-12
The Gnome Version is 2.30.2. Hopefully that helps. I'm hoping I can fix this soon. Tried to build a seperate Kernel for it and that didn't work whatsoever haha.

---

### Post by typhoon_tip on 2011-11-12
> **doxramos said:**
> The Gnome Version is 2.30.2. Hopefully that helps. I'm hoping I can fix this soon. Tried to build a seperate Kernel for it and that didn't work whatsoever haha.

I think you don't need to build a separate Kernel. If you have an hard drive available, please do the follow:

- Install a fresh copy
- Update everything
- Install FGLRX driver from ATI from AMD sites

---

