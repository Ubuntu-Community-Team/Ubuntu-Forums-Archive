---
title: "Problems with new Radeon x300 card"
date: 2010-10-27
forum: Desktop Environments
---

### Post by tnsmart on 2010-10-27
So I just got a new Radeon x300 dual head card with one VGA and one DVI and installed it on my Compaq Presario PC SR5130NX.  I have two Gateway 17" monitors hooked up, one through the VGA and run through the DVI (the monitors have both inputs).  When I start up the computer, it goes to the Login screen and is mirrored, as expected.  When I login to either the root user or the administrator user (the only two on there), I get a message for about 2 seconds before the panels load:"Could not apply the stored configuration for monitors.  X server does not support size required."  The screen remains in mirrored mode.  When I enter the Monitor Preferences and uncheck the mirror screens box, I get a message: "Monitor Resolution Settings had detected that that virtual resolution must be set in your configuration file in order to apply your settings. Would you like Screen Resolution to set the virtual resolution for you? (Recommended)."  If I click no, I get: "Your settings cannot be appled because the virtual resolution is not big enough to contain your screens."  If I click yes, it asks me to log out and then back in.  If I logout at any time, even without going to the Monitor Preferences, the screen gets scrambled with random colors everywhere and I can't see anything.

I do have the ATI Catalyst Control Center installed, but if I try to enter it, I get: "There was a problem initializing Catalyst Control Center Linux edition. It could be caused by the following.  No ATI graphics driver is installed, or the ATI driver is not function properly. Please install the ATI driver appropriate for your ATI hardware, or configure using aticonfig."  I don't know what aticonfig is but am guessing I'd run it through terminal.

Anyone know what I could do?  I am willing to try making an xorg.conf file if that is necessary but have been unsuccessful in the past. Any help is greatly appreciated.

---

### Post by tnsmart on 2010-10-28
So I came to my computer today, and now everything works fine, except when I logout.  When I logout, the upper half of the screens shows the background picture and the bottom half is a bunch of scrambled colors.  This lasts for a few seconds, and then the monitors shut off.

And I still have the same problem with the ATI Catalyst Control Center.

Anyone with ideas? Thanks.

---

### Post by alexandari on 2010-10-28
I never actually managed to run the Catalyst Control Center. I'm using the default ubuntu drivers,the other ones never did the trick for me. That's what I recommend...

---

### Post by tnsmart on 2010-10-28
Thanks for the reply.  I don't know too much about drivers, but I think I have the default ones.  Synaptic Package Manger tells me that I have these packages installed:
fglrx
fglrx-amdcccle
fglrx-modaliases
jockey-common
jockey-gtk
radeontool
xserver-xorg-video-ati
xserver-xorg-video-mach64
xserver-xorg-video-r128
xserver-xorg-video-radeon

Is there another driver I need?

And another note, I cannot active Normal or Extra Visual Effects. I get a  message: "Desktop effects could not be enabled."  Any ideas?

---

### Post by Mark Phelps on 2010-10-28
The card may be "new" to you ... but it's "old" to AMD/ATI -- so old that they dropped support for it a long time ago.

Installing fglrx drivers will not only NOT work with this card, it will likely hose up your display to the point that you will have to boot into a console to remove them.

IF you're using the open-source drivers, that's ALL that is available for that card and recent versions of Ubuntu.

---

### Post by clhsharky on 2010-10-29
tnsmart

Mark Phelps is correct, this will help.

 X/Troubleshooting/FglrxInteferesWithRadeonDriver
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)


Sharky

---

### Post by tnsmart on 2010-10-29
> **clhsharky said:**
> this will help.

 X/Troubleshooting/FglrxInteferesWithRadeonDriver
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)


Thanks for that.  I ran these commands:
```
  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
```I can now logout fine and see everything and the root user is fine, but the administrator user still has the right half of the right screen scrambled on the desktop.  I can put windows over it and they look fine, but the desktop looks bad and I would like to fix it.  Any more help would be appreciated.  Thanks again.

---

### Post by tnsmart on 2010-11-10
> **tnsmart said:**
> I can now logout fine and see everything and the root user is fine, but the administrator user still has the right half of the right screen scrambled on the desktop.  I can put windows over it and they look fine, but the desktop looks bad and I would like to fix it.  Any more help would be appreciated.  Thanks again.

Any new ideas on this?  My main problem is that I cannot enable any Visual Effects under the Appearance Preferences.

---

