---
title: "Compiz + Dell Inspiron 1501 (Gutsy)"
date: 2007-10-29
forum: Desktop Effects &amp; Customization
---

### Post by FMDragon on 2007-10-29
So I've done a fresh install of Gutsy and desktop effects wouldn't work. I installed restricted drivers and followed the instructions here, [http://ubuntu1501.blogspot.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html](http://ubuntu1501.blogspot.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html). Now, compiz kind of works (theres shadows under the windows), however, when I put compiz --replace in the terminal, it will out put three lines then hang on this:
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 gutsy

I'm also unable to open the settings manager from System -> Preferences -> Compiz Settings Manager. Any help? Thanks in advance.

---

### Post by FMDragon on 2007-10-29
bump

---

### Post by Dov on 2007-11-02
G'day fmdragon,
You no longer need to have a separate xgl login, in fact it is recognised as causing problems. Instead, just install the xserver-xgl package through the package manager (synaptic) in the Administration menu. Also install gnome-compiz-preferences if it has not already been installed. Hit Ctrl-Alt-Backspace to restart X and log in to a normal gnome session. Select "Appearance" from the Preferences menu and select "custom" from the Visual Effects tab. To use the configuration button on that tab, you will need to install the compiz-config-settings-manager package through Synaptic as well. This seems to be best installed after everything else. No idea why.

If you have any problems post back.

Enjoy!

---

