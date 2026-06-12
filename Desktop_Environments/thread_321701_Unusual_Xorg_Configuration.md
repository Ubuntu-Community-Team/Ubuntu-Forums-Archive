---
title: "Unusual Xorg Configuration"
date: 2006-12-19
forum: Desktop Environments
---

### Post by Beamerboy on 2006-12-19
Hello,

I am about to make hardware upgrades to my system, including a new cpu and a 3rd LCD monitor.

Currently I have dual 19" LCDs running in xinerama mode with NVidia official drivers.  Each monitor is driven from its own graphics card (of which I have 2 Nvidia 6600GT SLI PCI-E cards - although not running in SLI mode).

Also because I use cedega and it tries to maximise games across both monitors in xinerama mode, I use a second xserver on alt+ctrl+F8 with no window manager, to run cedega.  I launch this the following way:

sudo xinit /usr/bin/cedega -- :1 -config xorg-games.conf &

There are problems with my current methodology, in that everytime I reboot I must add a new xauth cookie for `hostname`/unix:1 before I can launch the cedega in the new xserver.  Furthermore, I am forced to run the new xserver as root and have been unable to find a way not to.

The situation is going to become even more difficult with the new setup.

For the new setup, I was to use 2 monitors in xinerama mode (giving me 1 desktop at 2560x1024 resolution as I currently have) and then I want to run the 3rd monitor as another desktop with resolution 1024x768.  Furthermore, I want the second (single monitor) desktop to run mythtv in full screen and to also run cedega in a second xserver accessable via alt+ctrl+F*n*, so I can switch between the MythTV Xserver and the Cedega X Server with ease.

I would like to be able to retain this configuration after reboots (without me having to add xauth cookies manually) and I would also like to be able to run the cedega Xserver as my normal user, and not as root.

I presume I will have to enable twinview as well in xorg.conf to use 3 of my existing 4 heads all at once.

I know this seems like a very unusual configuration and it is, but if anyone out there could possibly help me out with the solution, I would appreciate it.

Paladine

---

