---
title: "corrupt desktop windowing after removing Desktop Effects"
date: 2007-03-28
forum: Desktop Environments
---

### Post by bsmith1051 on 2007-03-28
I don't know if this is a bug or just an unfortunate side-effect to the order in which I installed/uninstalled things.  I've got a brand new from-scratch install of the Feisty beta on a system with an ATI X300 video card.  First thing I did was install the Restricted Driver hw-accel driver using the new System option; yeah, it worked!  This is the unofficial 'flgrx' open-source version, not the official ATI version, right?  Anyway, I then tried installing beryl and enabling Desktop Effects but it complained that the video driver was incompatible.  So I disabled the accelerated video driver, and also installed some other modules -- I think I installed 'compiz' and something else with 'gl' in the title?  Finally, I was able to enabled the 3D Desktop Effects.  

But I wasn't very impressed with them so I decided to return to the accelerated driver, to hopefully do some gaming.  I thought I disabled Desktop Effects, then re-enabled the accelerated video driver.  But now I've got weird corruption in the desktop windowing.

Nautilus windows no longer have the outside border (or controls), and applications have their menus up in the top row of the screen (covering the Ubuntu menus).  I haven't been able to figure-out any way to fix this!  I tried switching to other themes, but that only changed the colors. I've tried uninstalling beryl, compiz, and flgrxgl (name? it's the OpenGL accel desktop?) but still to no avail.  The only way I can close an application (and load another) is to use the File > Quit drop-down.

Any ideas what went wrong, or how to fix it?  I'm assuming I just need to reset some desktop config file...

---

### Post by bsmith1051 on 2007-03-28
so, I disabled the accelerated driver and now my desktop (but not the Firefox app) are blinking?!

UPDATE: re-enabled it and the blinking stopped.  hmm....

---

### Post by bsmith1051 on 2007-03-28
I think it must be the window manager?  I can't open the System > Preference > Windowing function.  it reports something about 'unknown' window manager.

---

### Post by bsmith1051 on 2007-03-28
**SOLUTION**
I hadn't uninstalled 'compiz' yet.  I think that this was preventing the default 'gdm' window manager from running.  As soon as I removed it (using Synaptic) the windows came back correctly.  I can also get into System > Preferences > Windows again.

---

