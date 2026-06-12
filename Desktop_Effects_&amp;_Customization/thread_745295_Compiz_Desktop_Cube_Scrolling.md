---
title: "Compiz Desktop Cube Scrolling"
date: 2008-04-04
forum: Desktop Effects &amp; Customization
---

### Post by mathenge on 2008-04-04
I have Ubuntu 7.10 installed and everything seems to be working well. I was able to spin my cube around by holding down the scroll wheel on the desktop. But I've since been playing with the configuration settings. I can still spin the cube by holding down the scroll wheel, but this behaviour happens everywhere.

What this means is that I've lost the ability to PASTE by clicking the scroll wheel when I'm using the terminal or any other application. Looks like my applications will never get the scroll wheel (Button2) click.

I'd like to restore the previous behaviour - the cube only spins when the desktop is clicked. Can anyone who has this behaviour working please tell me how they've configured ROTATE CUBE. This is under SYSTEM -> SETTINGS -> ADVANCED DESKTOP SETTINGS, then select ROTATE CUBE. Under ACTIONS.

Thanks for your help.

Andrew.

---

### Post by Locutus_of_Borg on 2008-04-04
Under Actions > Keybindings > initiate > the default is control + alt + button1

---

### Post by mathenge on 2008-04-13
Thanks for the response, but I finally solved this one. The problem was:

Ability to spin the cube using the middle mouse button, but only when it's pressed on the desktop. Which means that when the middle mouse button is clicked in an application (e.g., console) the application gets the click.

Two things need to be done. In Advanced Desktop Effects Settings, select Rotate Cube. For this item, under Actions, make sure that the "initiate" is either the default for the mouse button, or anything that you want, even "none." But not "Button2."

Next, select Viewport Switcher. Under Actions for this item, expand the item "Desktop-based Viewport Switching." Under "Initiate plugin action" make sure this is "Button2."

That's it.

To me it's strange that rotating the cube (which should be under the Rotate Cube plugin) is actually managed by Viewport Switching.

---

