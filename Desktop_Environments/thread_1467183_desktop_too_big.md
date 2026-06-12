---
title: "desktop too big"
date: 2010-04-30
forum: Desktop Environments
---

### Post by supertails on 2010-04-30
How do I change the desktop back to normal? I upgraded from 9.10 to 10.04 LTS and the desktop have changed in size and what to shrink it down. How do I do that?

---

### Post by 2hot6ft2 on 2010-04-30
Have you tried installing the restricted graphics driver (if one's available)?
System > Administration > Hardware Drivers

---

### Post by KinKiac on 2010-04-30
How do you mean to big?  Like too big as in everything seems smaller (icons, text, etc) or too big like it overscans and you end up with items outside the screen area?

The former can be changed by simply changing your resolution and the latter would probably be fixed with new graphics drivers.

---

### Post by supertails on 2010-05-01
Some of the icons left the screen but the icons are bigger. the window are bigger and so is the loggin window.

---

### Post by supertails on 2010-05-01
How do I give 2hot6ft2 thanks, I also thank KinKiac for trying but installing those drivers fix the problem. but one other problem I have is that the close, minimise and maximise bottoms are on the left side of the screen, that's going to take some getting use to but I'll see if I can switch them.

PS No more problems, turns out I had to change my Appearance Preferences.

---

### Post by infamous-online on 2010-05-01
> **supertails said:**
> How do I give 2hot6ft2 thanks, I also thank KinKiac for trying but installing those drivers fix the problem. but one other problem I have is that the close, minimise and maximise bottoms are on the left side of the screen, that's going to take some getting use to but I'll see if I can switch them.

PS No more problems, turns out I had to change my Appearance Preferences.

That's a new change about Ubuntu 10.04 the buttons are on the left, but to get them on the right side again open up a terminal and type in gconf-editor and once it's open go here > Apps > metacity > general and look for the button_layout and replace the values with this I'll make it bold so you'll know what you need to replace the values with **[COLOR="Red"]menu:minimize,maximize,close[/COLOR]**

---

