---
title: "Dual Monitors on Gutsy"
date: 2007-10-17
forum: Desktop Effects &amp; Customization
---

### Post by shanlot751 on 2007-10-17
Hey, my pc isn't fantastic but it gets me by. I'm trying to set up dual monitors on gusty RC1 and it's not working out too well for me. I'l enabled both monitors and told it to "extend" the desktop to the second. Through the new control panel entry. I've tried both proprietary and open source nvidia drivers. I am running compiz though even when it's off I don't have much luck (I have'nt tried turning it off then logging in and out yet though) I have an nvidia geforce mx 5400 agp and a geforce 5600 pci to 2 crts. Anyone care to explain what I'm doing wrong?

---

### Post by repawn on 2007-10-18
I am not sure how well this will work for you - but I had to enable support for two monitors today and I could not seem to do it well with the included screens app. I went to the terminal and typed gksu nvidia-settings

It should ask for your root password and then you can set your nvidia settings to twinview - I had to play with it just a bit to get the mouse to move correctly - you will probably want to apply the changes to xserver and then restart the xserver (I usually reboot.)

---

