---
title: "Shadows Stick in Compiz Fusion"
date: 2007-08-29
forum: Desktop Effects &amp; Customization
---

### Post by drewcoll on 2007-08-29
I am running Compiz Fusion and the shadows around the menus freeze and stick on screen if I move out of the boxes very fast.  Attached is an example.

Sometimes if I open the same menu on top they go away.

Thanks!

---

### Post by michael37 on 2007-08-30
You may have problems with your OpenGL accelerator: either a misconfigured xorg.conf or an incompatible driver.  Please post the output of glxinfo here.

---

### Post by andreag on 2007-10-28
I have the same problem, here is the output of glxinfo:

---

### Post by llib1234 on 2007-10-28
> **drewcoll said:**
> I am running Compiz Fusion and the shadows around the menus freeze and stick on screen if I move out of the boxes very fast.  Attached is an example.

Sometimes if I open the same menu on top they go away.

Thanks!

I also get the same thing. It happens usually with OpenOffice when the tooltips flash very fast as I scroll down the pages.
The only solution is to restart Compiz.
Or upgrade to the stable version 0.6.2 but it isn't available in any repos yet. 
We should send a note to Ubuntu repo maintainers asking for upgraded packages.

---

