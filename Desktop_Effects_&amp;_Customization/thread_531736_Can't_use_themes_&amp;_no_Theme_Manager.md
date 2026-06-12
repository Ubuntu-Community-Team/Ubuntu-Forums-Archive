---
title: "Can't use themes &amp; no Theme Manager"
date: 2007-08-21
forum: Desktop Effects &amp; Customization
---

### Post by timelessjazz on 2007-08-21
Hey..I'm still new to Linux..bare with me.  I installed beryl through the add/remove programs window, as well as the other to configure apps. listed as well.  I would like to apply themes, however I don't have the emerald themes manager...at least it doesn't she up in the manager drop down menu.  I tried to d/l aquamarine and emerald from the beryl website, and after entering ./configure i would get error messages...for Aquamarine, it said my X libraries can't be found.  For Emerald, it says:
 configure: error: Package requirements ( xrender >= 0.8.4                   gtk+-2.0 >= 2.8.0               libwnck-1.0                    pangocairo               libberyldecoration ) were not met:

No package 'xrender' found
No package 'gtk+-2.0' found
No package 'libwnck-1.0' found
No package 'pangocairo' found
No package 'libberyldecoration' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EMERALD_CFLAGS
and EMERALD_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I have no clue what these mean and what I need to do...any help would be appreciated! thanks!

---

### Post by FuturePilot on 2007-08-21
Did you try```
sudo apt-get install emerald-themes
```
It should also pull in emerald theme manager.

---

### Post by timelessjazz on 2007-08-21
beautiful...i have the themes manager now...but how do i apply the theme?

---

### Post by FuturePilot on 2007-08-21
Make sure Beryl is running then open the theme manager and just select a theme. It should apply it instantly.

---

### Post by timelessjazz on 2007-08-21
thanks a lot for your help...i figured it out...had to select emerald as the window decorator..

---

### Post by FuturePilot on 2007-08-21
No problem:D

---

### Post by timelessjazz on 2007-08-21
Ok maybe one more question...I notice that other beryl users when using the CUBE have a more zoomed out view...how do you set that? My view is close up and right against one side of the cube...couldn't find anything in the settings..

---

### Post by FuturePilot on 2007-08-21
That would be Compiz Fusion. I don't think that is adjustable in Beryl. At least I never found a way to do it.

---

### Post by StJimmy on 2007-08-25
To get a zoomed out view, open the beryl settings manager, then go to Desktop>Rotate Cube (enable it if it's not yet)>Behavior>General>Zoom.  I use 7.500. Hope this helped.

---

