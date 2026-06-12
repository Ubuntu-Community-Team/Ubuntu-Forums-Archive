---
title: "Ubuntu Flickering issue"
date: 2018-07-28
forum: Desktop Environments
---

### Post by mathewmanueljm on 2018-07-28
Hello

I recently installed the Ubuntu 18 version and having the flickering issue. 

Details of the install below,

cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.1 LTS"

uname -a
Linux matt-HP-Omni-120-1050xt-Intel-Leon-3C-NA-PC 4.15.0-29-generic #31-Ubuntu SMP Tue Jul 17 15:39:52 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

env | grep DESK
DESKTOP_AUTOSTART_ID=1090d8bc385de2c58f153280599835649800000019650007
DESKTOP_SESSION=Lubuntu
XDG_SESSION_DESKTOP=Lubuntu
XDG_CURRENT_DESKTOP=LXDE
GNOME_DESKTOP_SESSION_ID=this-is-deprecated

inxi -bG
System:    Host: matt-HP-Omni-120-1050xt-Intel-Leon-3C-NA-PC Kernel: 4.15.0-29-generic x86_64
           bits: 64
           Desktop: Gnome 3.28.2 Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop System: Hewlett-Packard product: HP Omni 120-1050xt Intel (Leon) 3C NA PC serial: N/A
           Mobo: Quanta model: 2AC5 v: 000 serial: N/A
           BIOS: AMI v: LEO_703 date: 09/08/2011
CPU:       Dual core Intel Core i3-2130 (-MT-MCP-) speed/max: 1596/3400 MHz
Graphics:  Card: Intel 2nd Generation Core Integrated Graphics Controller
           Display Server: x11 (X.Org 1.19.6 ) driver: i915
           Resolution: 1600x900@58.03hz
           OpenGL: renderer: Mesa DRI Intel Sandybridge Desktop
           version: 3.3 Mesa 18.0.5
Network:   Card-1: Broadcom Limited BCM43225 802.11b/g/n driver: wl
           Card-2: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 1000.2GB (0.7% used)
Info:      Processes: 259 Uptime: 21 min Memory: 1492.8/5873.4MB
           Client: Shell (bash) inxi: 2.3.56

---

### Post by mathewmanueljm on 2018-08-06
Does anyone have a solution for this? Downgraded to the version 14 still the same issue

---

### Post by kazakore on 2018-08-08
I think you need to describe better what you mean by "Flickering Issue".....

One suggestion I can make, although a total stab in the dark (and flickering is really not the right description) is to enable tear-free mode for the Intel graphics driver. I've needed to set it on every single computer I've had that uses Intel integrated graphics, like yours does, so it may help.

But as I say it doesn't quite meet your description, I'm going more on common issues I've had with similar hardware instead.

[https://askubuntu.com/questions/418398/tear-free-disabled-in-intel-graphics-tearing-in-xubuntu](https://askubuntu.com/questions/418398/tear-free-disabled-in-intel-graphics-tearing-in-xubuntu)

---

### Post by mathewmanueljm on 2018-08-08
there is continuous horizontal lines for 1 inch thick that keeps repainting, It is highly impossible to look at the screen. Kindof like when you try to take pictures on the old TV

---

