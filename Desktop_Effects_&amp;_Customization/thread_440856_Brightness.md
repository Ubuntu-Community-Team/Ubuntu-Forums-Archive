---
title: "Brightness"
date: 2007-05-12
forum: Desktop Effects &amp; Customization
---

### Post by brad1150 on 2007-05-12
How do I change the brightness. My monitor is kinda old and I need software contrast adn brightness to do anything now. I have an nvidia geforce mx4000 if that helps any.

---

### Post by Schalken on 2007-05-12
Try right clicking on a blank area on the panel > Add to Panel > System & Hardware / Brightness Applet.

---

### Post by brad1150 on 2007-05-12
It says "cannot get laptop panel brightness."

---

### Post by johnc4510 on 2007-05-12
brad, you can set your contrast and brightness via: nvidia-settings

In a terminal: Applications>Accessories>Terminal if using gnome, type this:

nvidia-settings

This will open a window to make adjustments:

Click on: xServer Color Corrections:  There you will find contrast and brightness settings

Next, to get these settings to load at startup, do this:

Go to System>Preferences>Sessions

Under Startup Programs click on the NEW button

Add this to the Command Line:

nvidia-settings --load-config-only

save and close all

Now when you boot, your brightness and contrast settings will automatically be used

good luck

---

### Post by brad1150 on 2007-05-12
It worked, thank you.

---

