---
title: "Visual effects settings not being remembered"
date: 2009-05-30
forum: General Help
---

### Post by hellocatfood on 2009-05-30
I'm using Ubuntu Jaunty on an ASUS A5SL laptop with an ati graphic card. I've downloaded the proprietary driver for the card and can now enable visual effects, but the problem is that it forgets this and any compiz  setting whenever I turn off my computer. So, I have to reenable them after logging in.  Is there an option I'm missing or is this a bug?

---

### Post by psychoelf on 2009-08-14
Have you tried installing the ccsm(compiz) settings manager in Synaptic?  

If so...you may want to try uninstalling all compiz related items in synaptic, logout, login, reinstall compiz, logout, login.

---

### Post by CatKiller on 2009-08-14
The quick-and-dirty method is to add ```
compiz --replace
``` to your Startup Applications, but it's a bit of a hack.

You can also set the /desktop/gnome/applications/window_manager/default and ../current GConf keys in gconf-editor to /usr/bin/compiz, although I'm not sure that it works for newer versions of Ubuntu.

The proper way is to update the gnome-wm default window manager setting, although I can't currently remember how to do that manually. I think that setting the above ../current GConf key makes it happen through some script voodoo, though.

---

