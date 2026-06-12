---
title: "[SOLVED] Vostro 1400 + Fresh Gutsy = weird issues"
date: 2007-10-30
forum: Dell  Ubuntu Support
---

### Post by aldenhg on 2007-10-30
I've just had to reinstall completely after a partition table error. (Word to the wise: OSX was meant for the Mac - Don't try it on the Vostro) I got everything working just fine (in fact, a lot fast than I did in feisty) but when I restarted it went into failsafe graphics mode. Crappy, right? Well, that was after I used the Nvidia installer to install the 8400m GS's drivers. I thought, "OK, that's fine. I'll just apt-get install nvidia-glx-new." So I did that and restarted X and I had my whiz-bang compiz effects back. Wary of my previous toubles, I rebooted and was once again thrown into failsafe graphics. I remembered having to add the driver to /etc/modules, so I did that and rebooted and was once again greeted by the failsafe graphics dialog. 
To break it down, I can install the driver and restart X and it'll work until I restart the computer. Keep in mind that this hardware was previously running just fine, though it was from an upgraded Feisty install and not a clean Gutsy as it is this time. 
Any ideas?

EDIT
I've made sure the right driver was selected in xorg.conf

---

### Post by analfabeta on 2007-10-30
Hi,

I have Vstro 1400 too, with Nvidia 8400m GS and Dell Wireless 1505 802.11n (bcm4328 rev. 03). I do a fresh install of gutsy and most thing works. But wireless dont. I'm trying use ndiswrapper, but dont have sucess with Vista driver (is needed XP drivers). Nvidia you can fix installing nvidia-glx-new, using restriced drivers.

---

### Post by aldenhg on 2007-10-30
Already tried it. I'll give it another shot, though. 
For your wireless, use the drivers I've attatched to this post. Uninstall the driver you're using now and then install the good one. I'd reccomend using the ndisgtk frontend if at all possible - it makes thing a little easier if you're wary of the command line. Make sure you add ndiswrapper to /etc/modules so it'll load when the computer starts up.

EDIT
No good. Tried installing through the Restricted Drivers manager and got the same result. The oss driver (nv) works fine for the time being, but I do like myself a little bit of Compiz and Half-Life 2.

---

### Post by aldenhg on 2007-10-30
After sifting through my /var/log/Xorg* files, I found the problem. Take a gander:
```
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: libGLcore.so.1: cannot open shared object file: No such file or directory
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
...
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
...
```
Which module isn't loading? Is it the kernel module of the driver? Anyone with more knowhow out there have any insight?

---

### Post by aldenhg on 2007-10-30
OK, I fixed it. For anyone with the same problem down the line, just use Envy. It's not the most graceful solution, but it fixed the problem lickety-split. I don't know it it'll screw me over when I upgrade to Hardy in six months, but that's a long way away to worry about right now.

---

