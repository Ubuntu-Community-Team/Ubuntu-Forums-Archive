---
title: "NVIDIA GForce FX 6200 Driver Installation Problem..."
date: 2006-04-30
forum: Gaming &amp; Leisure
---

### Post by sardopsycho on 2006-04-30
I am trying to install the linux drivers for my GeForce FX 6200 video card so I can play Doom 3 and Quake 4 - however the driver installation says I cannot install the driver in an X Window system - but I am using GNOME....so I am not sure what to do at this point.....

How do I load up into a command prompt only so I can install these drivers????

---

### Post by bluevoodoo1 on 2006-04-30
ctrl+alt+f1

sudo /etc/init.d/gdm stop

then continue on...
check out method 2 here... (might want to even print it out)
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

---

### Post by minisori on 2006-04-30
Why dont use the ones in repositories? They are prety easy to install:
sudo apt-get install nvidia-glx nvidia-kernel-common linux-restricted-modules

And when is done do:
sudo nvidia-glx-config enable

That would make your card to work with acceleration

---

### Post by jhonyrod on 2008-10-18
You can also install EnvyNG, this software automatically installs the lastest proper version of the nVidia driver, and configure it, just type in a terminal:
```
sudo apt-get install envyng-core envyng-gtk
```
For the GTK front end, and:
```
sudo apt-get install envyng-core envyng-qt
```
For the QT front end.
Once installed, you will see that program on the System Tools menu.
It will ask your password and then it will ask what do you want to do.
Just select "NVIDIA" on the left panel an then select "Install the NVIDIA driver (automatically detect hardware)" (or something like that), and then click on apply, wait a few minutes.
When done (if I remember correctly) it will ask you for reboot, if you are not doing something important, it would be better if you say yes, if you don't want to reboot now, or the message don't appears, the changes will take effect after you reboot your computer or restart the x server.
Once done you will be enjoying your hardware acceleration and the NVIDIA X Server Settings panel on System->Administration (you must run it as root if you want to save the change in the x server config file), where you can change the screen resolution, view the info of the card, override the antialiasing settings and many more features...

P.S. Sorry for my bad English and for the Spanish screen shot.

---

