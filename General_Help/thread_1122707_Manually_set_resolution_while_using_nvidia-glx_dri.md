---
title: "Manually set resolution while using nvidia-glx drivers"
date: 2009-04-11
forum: General Help
---

### Post by northern lights on 2009-04-11
In the course of f***ing around with my setup, I've accidentally chosen a screen resolution / refresh rate combo that's not supported by my monitor. After running```
dpkg-reconfigure xserver-xorg
``` I can enter gnome with the vesa driver. However, when trying to switch resolution with the *nvidia-settings* applet, it's telling me the driver's not in use. When reverting back to nvidia driver via```
nvidia-xconfig
```, my monitor goes black cause it doesn't support the current refresh rate set under *nvidia-settings*. What file do I have to edit to get out of this vicious cycle?

When I'm on vesa, I can't edit *nvidia-settings* when I'm on *nvidia-glx-177*, I can't change my resolution to what it was before cause my screen immediately blanks.

I need a hint on how to set my resolution under nvidia via the commandline.

Thanks in advance, Johannes

---

### Post by northern lights on 2009-04-13
In case anyone runs into the problem:```
xrandr -s 1680x1050
```(where 1680x1050 is my panel's native resolution) did the trick.

---

### Post by DenysT on 2009-04-13
The nvidia-settings were a mystery to me until someone somewhere on this forum showed me the way (thanks who ever you were I should have booked marked the post). Once you have the nvidia driver installed you then open a terminal window and enter gksudo nvidia-settings. Set the display properties you want and save the configuration. After reboot you should be able to use display settings to change settings for a session but not the configuration.

This not being able to easily configure video cards is a big drawback to using Linux. Something that people change out frequently should be easier to access and not require privileges to do in order to make it work. But then removing video drivers in Windows incorrectly before installing new video cards is a nightmare too.

---

