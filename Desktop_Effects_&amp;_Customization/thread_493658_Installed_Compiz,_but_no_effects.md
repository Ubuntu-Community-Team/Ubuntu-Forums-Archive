---
title: "Installed Compiz, but no effects"
date: 2007-07-06
forum: Desktop Effects &amp; Customization
---

### Post by 02wrx on 2007-07-06
HI all,
relatively new to ubuntu and linux.  anyway, i installed compiz fusion following the how-to.  i had the problem with the window decorations, but fixed that with some code in xorg.conf

so my system is running fine now, however, the compiz effects, like cube etc. are not working.  the alt-tab seems to work and minimize has an effect, but nothing else.  Its pretty irritating since I can't switch workspaces without using the mouse....

Please help, or point me to a post to restore the original desktop effects.

Thanks!

---

### Post by avik on 2007-07-06
I'm assuming you installed the Compiz Settings Manager, which should be in System->Preferences.  Go there and mess around with the settings, especially the keybindings.

---

### Post by 02wrx on 2007-07-06
The settings are the default ones after install.  So things like the cube are selected.  I also checked the key bindings and they should do something when I hit CTRL+ALT+ arrow, but nothing happens.

Just a note, I am using an nvidia card if that makes a difference.

Also, I followed the Compiz fusion how-to off of a fresh ubuntu 7.04 install, so I was hoping that it would work without any tweeking.

---

### Post by psyopper on 2007-07-06
Try changing to the Flat-File backend. This fixed a few keybinding issues I was having.

When you first open Compiz Config Settings Manager (ccsm) in the lower left corner is a button labeled "Backend and Profile ->"

Click this button and select "Flat-file COnfiguration Backend" from the Backend drop down menu.

Restart Compiz and see if your bindings are working. Caution: You may loose a few of your settings and have to go back through and reset them. It doesn't harm anything, it's just a little annoying.

---

