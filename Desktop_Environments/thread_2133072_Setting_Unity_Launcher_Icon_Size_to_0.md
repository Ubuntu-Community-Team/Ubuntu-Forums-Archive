---
title: "Setting Unity Launcher Icon Size to 0?"
date: 2013-04-06
forum: Desktop Environments
---

### Post by Xanza on 2013-04-06
Is there a way to set the icon size to 0 to permanently hide it?

---

### Post by 3rdalbum on 2013-04-07
No, this isn't what you want. It would make the icons zero width, but you'd still see the launcher.

A better method is to set the Launcher Reveal Edge Responsiveness to 0 and the Launcher Reveal Pressure to maximum, and Hide Launcher to "Autohide". This should make the launcher never appear unless you hold or tap the Super key.

You can disable the Super key to show the Launcher, and it's quite obvious in CCSM how to do it, but you'd be left with nearly no way to bring it back. And if you have no Unity launcher and no Dash, then you'd probably just be happier changing to a different desktop.

Edit: You need to use Compizconfig Settings Manager; the options are inside the Unity Plugin bit. Be very, very, extremely careful with Compizconfig Settings Manager and don't fiddle with anything except what I've advised. You can break your desktop if you're not careful.

---

### Post by gnugen on 2013-04-11
If you do not want to just see the launcher, you can autohide the launcher by going to system settings, clicking on appearance, clicking on the behaviour tab and make sure the autohide launcher option is enabled. If you want the icon size to zero, I think you can use Ubuntu Tweak to do that.

To get ubuntu tweak, run these commands:
> 
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

For more information on installing Ubuntu Tweak, visit this website [http://www.noobslab.com/2012/11/install-ubuntu-tweak-082-in-ubuntu.html](http://www.noobslab.com/2012/11/install-ubuntu-tweak-082-in-ubuntu.html)

---

### Post by Frogs Hair on 2013-04-11
Ubuntu Tweak and the Unity tweak Tool both have 32x32 size limits.

---

