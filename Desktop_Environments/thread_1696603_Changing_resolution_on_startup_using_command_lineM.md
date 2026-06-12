---
title: "Changing resolution on startup using command line/Monitor Settings"
date: 2011-02-27
forum: Desktop Environments
---

### Post by Sunships on 2011-02-27
Hello,

I have performed a fresh installation of lubuntu 10.04, and have installed gdm to attempt to recapitulate a standard ubuntu installation.

When I start up my default screen resolution is 1024x768.
I can use the lxrandr application (System->Preferences->Monitor Settings) to set the resolution to 1280x800, which is much more pleasant. However, when I reboot, the resolution goes back to 1024x768. If I try:

xrandr -s 1280x800 I get the message: Size 1280x800 not found in available modes

..which doesn't make much sense.

I have tried running lxrandr as a command with a similar syntax, but this only brings up the Monitor Settings configuration window. 

Ideally I would like to find a command which either:

sets the default resolution to 1280x800, so it always adopts this on start up

or

opens Monitor Settings and changes the resolution to 1280x800, and can be run using a script.

Can anyone help?

Thank you!

---

### Post by Sunships on 2011-03-04
*bump*

---

### Post by mikewhatever on 2011-03-04
I think the best possible solution would be to create a custome xorg.conf file.
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Since xorg.conf doesn't exist at all in most modern distros, you might want to start with generating it.
[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

---

### Post by Krytarik on 2011-03-04
Try setting up xrandr to change your resolution at startup of GDM by following this guide:
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions")

It's generally much easier than setting up a xorg.conf, and those  doesn't even necessarily work, as was the case at a machine I am  maintaining.

---

### Post by Sunships on 2011-03-05
Thanks guys, those look like useful links...but the problem seems to have resolved itself somehow! I haven't done anything...we'll see if it changes back, and if so, if those instructions you posted help.

---

