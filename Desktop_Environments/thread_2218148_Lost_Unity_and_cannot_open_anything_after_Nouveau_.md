---
title: "Lost Unity and cannot open anything after Nouveau -&gt; NVidia tested driver on 14.04"
date: 2014-04-19
forum: Desktop Environments
---

### Post by derekcentrico on 2014-04-19
Funny thing, I did a complete re-install after this occurred yesterday.  I didn't realize it was the driver.  Now, I know.

So, I switched to the NVIDIA tested proprietary driver and rebooted.  Now, my desktop has my background and the desktop files.  However, there is no unity bar.  Also, nothing happens when I click on the taskbar.  The power button doesn't do anything.  I cannot get into system settings to revert back.

Any suggestions to save myself from reinstalling Ubuntu all over again?

All help is appreciated.

---

### Post by grahammechanical on 2014-04-19
You do not need to re-install. At the Grub boot menu open Advance Options for Ubuntu and select Recovery mode. At the Recovery menu select Resume. That should get you to a working desktop. Then do some more experimenting with the video drivers. You can also try these commands

Reset compiz
```
dconf rest -f /org/compiz/
```

Reset Unity
```
setsid unity
```

By the way, if we have desktop wallpaper a right click on the wallpaper will give us the option to Change Desktop Background. That option opens System Settings and from there we can get to Software and Updates>Additional Drivers tab.

Regards

---

### Post by derekcentrico on 2014-04-19
Okay, so resume didn't work.  I got a blank screen for 5 mins or so.

I'm skipping the full reset of the desktop GUI at this point.

I tried #3.  I can get into the system settings and toggle a new driver.  However, it forces me to authenticate.  The laptop keybaord and the USB keyboard cannot type in the box.  When I click on the box, a cursor does not show in it like normal.

---

### Post by derekcentrico on 2014-04-19
Okay, I'm back in business.

I entered console, and did apt-get remove nivida-331.

A reboot went back to Nouveau drivers and everything is normal.

Now to test nvidia-331-updates.

EDIT:
And, all the latest nvidia drivers cause problems with this setup.  So, I guess I'm sitting with Nouveau for now.  Damn.

Anyone have an idea how to get solid NVidia drivers working with 14.04?  I assume my optimus setup is the problem since NVidia drivers work fine on desktop.

---

