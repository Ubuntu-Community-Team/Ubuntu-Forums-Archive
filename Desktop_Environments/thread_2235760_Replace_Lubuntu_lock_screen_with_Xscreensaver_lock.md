---
title: "Replace Lubuntu lock screen with Xscreensaver lock screen?"
date: 2014-07-22
forum: Desktop Environments
---

### Post by OzzyFreakDude on 2014-07-22
As the title suggests, I'm trying to replace my Lubuntu (14.04) lock screen with the Xscreensaver lock screen.

The Lubuntu login screen and lock screen are basically one in the same, so it's also possible that I'm automatically getting logged out after a time period, in which case help figuring out how to disable that instead would be awesome.

At first the Xscreensaver lock kicks in, then after an uncertain amount of time I basically have to login/unlock through the Lubuntu screen AND unlock from Xscreensaver.  Ideally I want to only have to unlock from the Xscreensaver screenlock.

I had the same issue while using Ubuntu with Unity, but this was never an issue while using Mint Mate.

Things I've tried:
-Updating the screen lock *.desktop file to point to the Xscreensaver lock command
-Disabling Light Locker via the Light Locker GUI
-Uninstalling gnome-screensaver

---

### Post by Zarnaik on 2014-10-08
Might be late, but better now than never. 
A very simple way to stop light-locker from working is to just uninstall the package. gnome-screensaver is, afaik, unrelated to locking the screen.

sudo apt-get purge light-locker

If you're uninstalling the locker wholly, it would make sense to also remove the light-locker-settings package.
I believe xscreensaver used to be the default, so you can install that for locking purposes/screensavers.

---

