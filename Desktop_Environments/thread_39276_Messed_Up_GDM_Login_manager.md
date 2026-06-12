---
title: "Messed Up GDM Login manager"
date: 2005-06-04
forum: Desktop Environments
---

### Post by hal8000 on 2005-06-04
I've messed up the gnome login manager, or to be more precise, when booting ubuntu, I am now presented with a login prompt.

If I type startx gnome 2.10 will load, If I type sudo gdm the gnome display manager will
load.

Had a look at /etc/inittab it is set to init2.

Where should the call to load gdm be placed? in ~/.xinitrc ?

Prior to this I was running sysvconfig and turned off some services I do not need,
probably something I turned off affects gdm?

Thanks in advance for any help on this one.

---

### Post by hal8000 on 2005-06-05
Very stupidly , I had disabled the gdm service, (which was the first thing I checked).
Next time I'll get some bigger glasses.

---

