---
title: "Live CD boots into Classic...questions"
date: 2011-07-10
forum: Desktop Environments
---

### Post by mystika1 on 2011-07-10
Hi,
I am thinking of switching to Ubuntu and have questions. From what I gather I apparently have hardware issues that are preventing me from booking the live cd into the unity desktop environment. My graphics card is an Nvidia 8800gtx which does indeed have 3d capabilities. Does this mean that I if I install Ubuntu 11.4 it will still  install gnome instead of Unity? If this is the case...should I not bother with Ubuntu? From what I have read the next release of Ubuntu will only boot into unity so where does that leave me in six months if I can't install unity?

Forgive my ignorance....I have previously used Kubuntu, Aptosid, Chakra and a few others all in KDE. I am just looking for something different to check out. 

Thanks,

Penny

---

### Post by Blasphemist on 2011-07-10
There are others that can explain this better than I but I'll give this a shot. The Live CD runs a program described in this link to see if it should present Unity or the classic gnome desktop. [https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

On that page you'll see the recommendation for Nvidia systems to use the proprietary driver or the experimental nouveau 3D driver. It seems the default open source nouveau driver that must be being used by default is falling back to classic. It could well be that you could use grub to set some parameters at the start of boot that would allow the live cd to present Unity. Or you could create a custom iso. 

What you have heard is not the case. The next release of Ubuntu provides Unity 3D and 2D as well as the Gnome Shell desktop environments. Gnome 2.x is no longer in development so all distro's will eventually move away from it unless that changes.

I recommend that you post to this sticky thread as the OP is very good with nvidia graphics and can likely give you a much better answer. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by coffeecat on 2011-07-11
> **mystika1 said:**
> Does this mean that I if I install Ubuntu 11.4 it will still  install gnome instead of Unity? If this is the case...should I not bother with Ubuntu? From what I have read the next release of Ubuntu will only boot into unity so where does that leave me in six months if I can't install unity?

11.04 and 11.10 are very different things with regard to gnome, so let's take them separately.

Ubuntu 11.04 is built with gnome. You can't have a choice of installing either Unity or gnome, because Unity runs on top of gnome. Unity is simply a compiz plugin. But you do get the choice of logging into either Unity or classic gnome in 11.04. If your graphics-hardware/driver combination doesn't support 3d, the system automatically falls back to classic gnome. This happens with all nvidia cards in the live 11.04 session because the version of the open source nouveau driver that comes with 11.04 doesn't support 3d out-of-the-box. Your nvidia card is quite capable of running Unity, but it needs the proprietary nvidia driver or the experimental libgl1-mesa-dri-experimental package which works reasonably well with some/many nvidia cards. There is a way of enabling 3d in the live session (with the experimental driver) but it's a fiddle, so in practical terms you need to create a permanent installation of 11.04 before you can get 3d/Unity with a nvidia card.

11.10 is built on gnome3 rather than gnome2 that 11.04 comes with. Your default desktops will be Unity 3d (for hardware that will run it) and a fallback Unity 2d. No gnome shell and no classic gnome - at least in a default installation. However, gnome3 shell and a fallback gnome panel desktop are only a few clicks away in the package manager. You won't get them in the live session, but they can be installed once you have installed a system to hard disc. The fallback gnome panel desktop is based on gnome3 but will look and feel somewhat like classic gnome. It should keep people who prefer classic gnome happy enough, except that many of the old panel applets won't work with it - if I understand things correctly.

Nvidia in 11.10: 3d capability in the default nouveau driver will come in-the-box as default in 11.10 which should give most nvidia users Unity 3d without having to install the proprietary driver although, no doubt, many will wish to.

---

### Post by Bucky Ball on 2011-07-11
KDE will always be KDE. That's not changing. Only Ubuntu, and you can run Gnome in 11.04 as well as Unity anyhow. You just choose 'Classic Gnome (or Ubuntu)' from 'Sessions' at log in. Gnome3 is coming next so Unity will never be your only option. (Have an 11.04 Xubuntu install - which uses Xfce -  so can't help with whether 11.04 will use Unity on install but should be using it on 'try Ubuntu' option from LiveCD anyhow. Don't know what's happening there).

---

### Post by mystika1 on 2011-07-11
Thanks everyone for helping me understand things. I think it is time for me to try out Ubuntu. I remember the days when I was using Kubuntu when it only took about an hour to have my setup including printer completed in about an hour:P...can't beat that. I am sure Ubuntu will be just as fast. Beats spending weeks getting a system configured.

Thanks,

Penny

---

### Post by Bucky Ball on 2011-07-11
Kubuntu *is* Ubuntu with KDE desktop environment instead of Gnome. They all use same Ubuntu kernel. If Kubuntu worked fine, Ubuntu should be, too.

(Xubuntu fastest of the three and you can add what you want once installed. Uses Xfce desktop environment and that won't change to Unity.)

---

