---
title: "Reinstalling Video Drivers Properly (unusable system)"
date: 2009-02-22
forum: General Help
---

### Post by [TCK] on 2009-02-22
It's a bit of a long story, but the tl;dr version is I've tried reinstalling fglrx for my ATI card and in trying to configure it for my dual monitors the GUI won't boot.  I need to clean my system of graphic drivers so I can start again and do things the right way.

The long version:

Kubuntu 8.10 w/ KDE 4.2 (previously 8.04 w/ KDE 4.1)
ATI X1600 graphics card

Three days ago after rebooting I noticed that my system was acting sluggish, and video was unplayable (for more information see [this post]("http://ubuntuforums.org/showthread.php?p=6775003#post6775003")).  I tried uninstalling and reinstalling the fglrx driver multiple times, deleting remnants of the previous installs but nothing would solve the problem.  In addition attempting to do these things resulted in a lot of unexpected behaviour such as Catalyst Control Center not opening, jockey-kde not responding to activating/deactivating proprietary drivers and glxinfo/glxgears giving me an error message.  In my frustration I decided to install the 9.2 drivers from the ATI website.

This worked to a point, the system booted up okay though limited to only one monitor, so I ran 
```
aticonfig --initial=dual --screen-layout=right 
```
which upon rebooting causes flickering on one of my screens as Kubuntu tries to load KDE4, which it eventually gives up on.  

Basically I need to find a way to properly get Kubuntu to recognise two monitors, and to do so I believe I need to completely clean my system of my previous attempts to install graphical drivers.  I understand that ATI cards are generally uncooperative with Linux but I've got it to work before all this so I know it can be done.  Any help will be much appreciated!

---

