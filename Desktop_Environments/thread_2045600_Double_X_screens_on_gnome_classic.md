---
title: "Double X screens on gnome classic"
date: 2012-08-21
forum: Desktop Environments
---

### Post by apowmit4 on 2012-08-21
I'm running 12.04 on my Macbook Pro 6,2 with the gnome classic desktop.  I was messing around with an external monitor trying set it up with separate x screens vs. twin view.  The problem is now I am getting double x screens on the laptop display.  Two application menus, two logout icons, etc. 

I've tried to reconfigure my xorg.conf file, uninstall and re-install the gnome classic environment, but I cannon get the double x screens to go away.  Note that there is no problem  if I log in with the default unity desktop.

Any suggestions?

---

### Post by mayonezo on 2012-09-15
Hey, I got the exact same problem after messing with multiple monitors running debian wheezy. Also my 9 workspaces were spread over a 3x3 grid. Now it is a 1X9 grid. Did you find a solution to the problem?

---

### Post by mayonezo on 2012-09-15
Okay, got it working again:

Alt+F2 and enter:
dconf reset -f /org/gnome/gnome-panel/

This will reset gnome panel and its settings.

---

### Post by guikubivan on 2013-02-08
> **mayonezo said:**
> Okay, got it working again:

Alt+F2 and enter:
dconf reset -f /org/gnome/gnome-panel/

This will reset gnome panel and its settings.

Holy crap, thank you! It took me like an hour and a half to figure out why my windows weren't using the whole screen! I was confused more because I have a dual monitor setup and had to modify the primary monitor through xorg.conf (instead of xrandr). At first I thought my resolution was not right. Anyways, just adding some keywords for google and thanks again!

---

