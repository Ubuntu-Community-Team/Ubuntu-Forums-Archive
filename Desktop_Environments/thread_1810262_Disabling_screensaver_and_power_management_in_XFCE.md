---
title: "Disabling screensaver and power management in XFCE"
date: 2011-07-22
forum: Desktop Environments
---

### Post by haresear on 2011-07-22
Because Ubuntu 11.04 is a bit heavy for the capabilities of my older desktop hardware, I am in the process of switching over to Xubuntu 11.04 going forward. I found the "sleep inhibit applet" very useful when I was using the Gnome DE, and was searching for a replacement in XFCE that doesn't require installing a bunch of Gnome libraries. I found a description of "caffeine" as a utility that seems to be what I'm looking for, but when I added the caffeine ppa to my repositories, and select it for installation in Synaptic, it wants to add a long list of Gnome-related components.

Is there any quick way to temporarily disable the screensaver and power management functions in XCFE that doesn't depend on Gnome?

Thanks.

---

### Post by neu5eeCh on 2011-07-22
You've tried Settings Manager ---> Screensaver? You can turn off the Screensaver and uncheck Power Management under the Advanced tab.

---

### Post by haresear on 2011-07-22
> **VTPoet said:**
> You've tried Settings Manager ---> Screensaver? You can turn off the Screensaver and uncheck Power Management under the Advanced tab.

Yes, thanks, that's what I'm doing for now, but it takes seven clicks to accomplish (seriously, I counted). I was hoping for a one-click solution.

---

### Post by haresear on 2011-07-23
> **VTPoet said:**
> You've tried Settings Manager ---> Screensaver? You can turn off the Screensaver and uncheck Power Management under the Advanced tab.

I've just discovered that unchecking Display Power Management in Screensaver settings doesn't actually work -- the display still goes into standby. Not sure if the GUI interface isn't working or some other program is controlling the monitor power management.

---

### Post by hhh on 2011-07-23
@haresear, I bet even money that that is screen-blanking kicking in, which can be a pain to disable. Try this though... for your current session, copy/paste these commands one at a time in a terminal...```
xset -dpms
xset s noblank
xset s off
```

If that works and you want it to persist on reboot, you'll need to create/modify the file /etc/X11/xorg.conf. If you don't have the file create it and add the following, if you do have that file add the following under Section "Monitor", leaving out the Section "Monitor" and EndSection lines...```
Section "Monitor"
Option          "NODPMS"
EndSection
```

Reboot and see if it works. If not, try these lines, again leaving out the Section/EndSection lines if you already have those sections and rebooting afterwards...```
Section "Monitor"
Option          "DPMS"
EndSection

Section "ServerLayout"
Option          "BlankTime"     "0"
Option          "StandbyTime"   "0"
Option          "SuspendTime"   "0"
Option          "OffTime"       "0"
EndSection
```

---

### Post by haresear on 2011-07-23
@hhh, thanks -- I'll give it a try.

Edit: "xset -dpms" works fine. Thanks for pointing me to this solution.

---

