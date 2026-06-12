---
title: "&quot;Desktop effects could not be enabled&quot;"
date: 2009-03-03
forum: Desktop Environments
---

### Post by dtom2444 on 2009-03-03
i was running ubuntu 8.10 for about two months with little to no hiccups. So i decided to allocate more memory to my ubuntu partition by using GParted. HUGE mistake. Ever since then, almost everything has changed.

But to get to my question, Compiz used to run perfectly. All the effects ran fine, i had Visual Effects turned all the way to Extra, it was beautiful. But now, even after enabling the effects i want in Compiz, none work. I figured it must be in the Visual Effects tab under Appearance. It's selected as none and when i select any other options, it tries to load, the screen flashes and then i get the error message, "Desktop effects could not be enabled."

Can anyone tell me what could've caused this change? is there a solution to this?

---

### Post by dtom2444 on 2009-03-04
Update:

ok, so after running "sudo compiz" i get this info:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to load theme "Mac4Lin_GTK_v1.0_RC": Failed to find a valid file for theme Mac4Lin_GTK_v1.0_RC

the "Mac4Lin_GTK_v1.0_RC" part is part of a theme i attempted to install which gives your desktop a "Mac-like" look. The problem was that i was supposed to extract the files to the home folder then run two lines of codes. i did so and got a message saying that the theme was successfully installed but it really wasn't. 

so, now it seems as though it's trying to load this theme that's not really there and it's going to metacity. i don't even know what metacity is but i'm guessing it loads themes (?). 

Is there anyway to change metacity's settings so it doesn't load this theme?

How can i uninstall a theme that isn't there? 

Please help!

---

### Post by 73ckn797 on 2009-03-05
Same issue here. Compiz cannot be enabled. Was running kernel 11 and went back to kernel 9 with same results. I had compiz turned off and was running Metacity. I have a menu selection for Metacity but nothing happens when I click on it.

EDIT: Solution found.

Go to this site and follow instrutions.

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)     

Here are the results on my system.

./compiz-check

```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G71 [GeForce 7900 GS] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Another compositing manager in use. 

Would you like to know more? (Y/n) y

 The default window manager of GNOME has its own compositing manager to
 provide basic desktop effects.
 If this one is in use, Compiz will not be able to run. 

Do you want to disable GNOME's compositing manager? (Y/n) y
```

I was able to get effects to work after this. Metacity is the Gnome desktop manager and has to be turned off before Compiz will work.

---

