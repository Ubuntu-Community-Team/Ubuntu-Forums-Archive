---
title: "Ubuntu not displaying anything"
date: 2007-12-26
forum: Desktop Effects &amp; Customization
---

### Post by Ozenbac on 2007-12-26
So I tried to install some eye candy, (compiz) and I broke my box.  I start up but once grub gets going the monitor goes blank and eventually just goes to sleep.  As far as I remember, (This all happened before x-mas), all I messed with was a ~/.Xsession file, which I have since removed, and I installed xserver-xorg and got rid of xorg-common.  Both of which I have tried to reverse.   I've tried installing gdm and every other viz package I could think of but nothings working.  help?

---

### Post by kwacka on 2007-12-28
Try typing:  sudo dpkg-reconfigure xserver-xorg      and follow the instructions.

Then either re-boot computer or type:  sudo /etc/init.d/gdm restart

---

### Post by Ozenbac on 2007-12-29
Thanks, I got fed up and just did a wipe and clean install, but I'll remember this for when I break everything again.

---

