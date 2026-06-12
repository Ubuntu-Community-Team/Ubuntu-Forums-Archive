---
title: "Am I using the best driver for ATI3850?"
date: 2009-06-14
forum: General Help
---

### Post by ctownclowns on 2009-06-14
Did some quick searching so forgive this newb if I haven't dug enough.  I noticed when moving around a windowed firefox page graphically there was some jitter.  I installed the FGLRX graphics driver and noticed when I opened firefox a nice little graphic was displayed so I've I'm assuming that's an improvement, however the jittering is still there.  It's not bad, just thought it was graphic driver related and would be smoother with the driver update.  I haven't done anything GPU intensive yet.

This brings me to the question is the FGLRX the best driver available or is there anything newer?  Will the FGLRX be better then any driver on AMD's page?  Does the FGLRX driver take full advantage of the card and provide good improvements or am I better rolling with intergrated vid and moving the card to a windows rig for gaming.  I'm assuming there are some games out there I may be interested in trying.  Any input is appreciated.

---

### Post by TrakerJon on 2009-06-14
ATI and Nvidia Drivers and Desktop Effects

The new Ubuntu 9.04 Jaunty Jackalope system comes with a Nouveau display graphic driver by default and the advanced effects cannot be used. If you've already tried to enable restricted Ubuntu drivers and ATI/nVidia cannot be found in the list try installing the ATI/nVidia driver with this tutorial:

1. Run Applications/Add/Remove
2. From the left menu choose System Tools
3. Next from the right menu, find and select for install: Desktop Effects (Compiz Setup) and ATI/Nvidia binary X.org Driver (nVidia could be version 173 or 177). Selecting the driver will get the list of supported graphics cards.
4. Click Apply Changes and after installation go to System/Administration/Hardware Drivers
5. The system will search for available drivers, choose the recommended option from the list and activate the driver by clicking Activate.
6. Restart your system and the new ATI/nVidia graphic display driver will be in use.

---

### Post by cmost on 2009-06-14
If you want newer ATI, (especially Intel) and other graphics drivers, then simply add this repository to your /etc/apt/sources.list:

## Upgraded video drivers for Ubuntu
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main

After saving the file, issue apt-get update && apt-get dist-upgrade as root.

Also, I fixed a lot of my display issues by adding my own tweaked xorg.conf to /etc/X11

Jaunty, by default, utilizes a very minimalistic xorg.conf because the new xserver 1.6 auto detects everything.  But, as they say about the "jack of all trades"...it's master of none!  I recommend tweaking your xorg.conf for optimal performance with ATI video cards.  Here's some sources to help you figure out what to place in the file and where!  Good luck!

Ubuntu Forums - Post your xorg.conf graphics card tweaks
[http://ubuntuforums.org/showthread.php?t=849422](http://ubuntuforums.org/showthread.php?t=849422)

Modify xorg.conf for better performance
[http://www.tuxradar.com/content/modify-xorgconf-better-performance](http://www.tuxradar.com/content/modify-xorgconf-better-performance)

Gentoo Wiki - fglrx
[http://en.gentoo-wiki.com/wiki/Fglrx](http://en.gentoo-wiki.com/wiki/Fglrx)

Compiz-fusion forums - tweaking xorg.conf for best performance
[http://forum.compiz-fusion.org/showthread.php?t=6563](http://forum.compiz-fusion.org/showthread.php?t=6563)

---

### Post by lamego on 2009-06-14
> This brings me to the question is the FGLRX the best driver available or is there anything newer? Will the FGLRX be better then any driver on AMD's page? Does the FGLRX driver take full advantage of the card and provide good improvements or am I better rolling with intergrated vid and moving the card to a windows rig for gaming. I'm assuming there are some games out there I may be interested in trying. Any input is appreciated.
In general terms FGLRX is the best driver for the supported AMD/ATI models, because it's provided by ATI and the version available on the repositories what tested during the development phase.
The newest version availble on AMD's page could be better or worse, since it was not tested unlike the driver from the repositories.

---

