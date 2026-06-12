---
title: "Gnome explodes.. literally"
date: 2006-02-02
forum: Desktop Environments
---

### Post by finalzero on 2006-02-02
Hi,

I have got Ubuntu 5.10 running with the latest kernel (2.6.12-10-686-smp) and I have installed the latest nVidia driver (v81.78 using the offical installer method).

Everything works fine and I have configured my xorg.conf to use TwinView so I can have dual screen desktop (3200x1200 desktop space); also 3D works fine and I enabled Hardware Accleration on my graphics card in the xorg.conf file which also works fine and is reported by the nVidia gui app.

Unfortunately when I log out the whole screen just turns to mush, I get garbled images on both screens and the whole system completely dies, only way to recover is to soft reset the PC and let Ubuntu load back up.. this is very annoying.

Right now to logout I am having to go to the console and stop gdm to kill the X and then using startx to get back in so it looks like gdm is causing some issues with the nVidia drivers.  I have a similar setup in Debian 3.1 without any problems (gdm, gnome 2.10.1 etc).

My current setup:

2 x Intel P4 Xeon Prestonia CPU's clocked at 3.5ghz each
ASUS PC-DL Deluxe (latest bios etc)
2 Gigabyte DDR-400 ram (4 x 512MB modules)
1 x Maxtor Ultra ide drive (boot device)
2 x Maxtor Ultra's setup in Raid 0 (data drives)
nVidia 5950 Ultra AGP x8 Graphics card (stock settings, no overclock or tweaks)

Thanks in advance,

Fz

---

