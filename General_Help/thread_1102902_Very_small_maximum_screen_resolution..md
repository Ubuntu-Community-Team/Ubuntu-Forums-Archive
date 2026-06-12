---
title: "Very small maximum screen resolution."
date: 2009-03-22
forum: General Help
---

### Post by Zackel on 2009-03-22
Hello.
After i first installed ubuntu...same as now the monitor was unknown. It had a maximum resolution of 800x600. 
I've installed the drivers for my geforce ti 4800 video card and most of the cool ubuntu visual effects work pretty well but the maximum screen resolution available now is 640x480.
My monitor is a benq fp71g+ and i know for sure that it can support 1024x768(75 hz) resolution. 
Tried many solutions: reconfiguring the xorg file...but nothing about changing the screen resolution came up there.
tried xrandr ...managed to add a new modeline resolution but just couldn't use it, most likely because i'm new to linux and don't understand the terminal commands very well.
I would very much appreciate some detailed help on this or some other easy way to get around it.
Thanks.

---

### Post by wfp on 2009-03-22
If your using hardy you could try hitting alt+f2 then in the dialog box type in gksudo displayconfig-gtk, and pick generic monitor and set the resolution there. If your on intrepid you could try installing nvidia x server settings. Open a terminal and type sudo apt-get install nvidia-settings

---

### Post by CatKiller on 2009-03-22
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

---

### Post by Zackel on 2009-03-22
well i finally managed to fix a great deal of it :).
Searched for specs of my monitor stopped gdm and edited xorg.conf with nano saved it and started the gdm again i'm not sure what this means but it worked.
I can finally set the resolution to 1024x768 but refresh rate remains 50 :).

---

### Post by CatKiller on 2009-03-22
> **Zackel said:**
> I can finally set the resolution to 1024x768 but refresh rate remains 50 :).

That appears to be a problem with Compiz, as far as I can tell. It generally seems to report refresh rates in the 50s, even though it's actually higher. I don't know why.

---

