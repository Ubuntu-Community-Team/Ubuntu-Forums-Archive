---
title: "unsupported apps"
date: 2008-05-03
forum: Desktop Environments
---

### Post by lakelovers on 2008-05-03
I searched this but didn't find a thread. I want to upgrade 7.10. In reading the conditions of upgrading, I understand that if unsupported apps are installed they may cause problems during the upgrade. My question is how can I find unsupported apps (if any) that I have installed in 7.10? I selected all of the software sources sometime ago, and I don't know whether there are any unsupported apps that I may have installed while fooling around. If I can identify the unsupported apps in Synaptic I'll remove them.

**Edit:** I searched Synaptic for "unsupported applications" and they popped up. Don't know why I didn't do it before. Anyway, the only one installed is X11 Athena Widget library. When I select *Mark for Complete Removal* as whole slew of applications show up gdeb, a number of gnome apps, and kde apps, To remove all of these sound dangerous. Or, would I just be removing X11 elements of those apps. Or, should I cross my fingers and go ahead updating 7.10?

---

### Post by luisromangz on 2008-05-03
The warning refers mainly to applications installed using thir-party repositories in my opinion. You shouldn't be worried if it isn't your case.

---

### Post by Zorael on 2008-05-03
You could give it a go. Just jot down the name of the package so you can forcefully install the Hardy version if stuff doesn't work.

If you get resolution errors, you may want to recreate your X configuration file. This'll be after upgrading, but I'm mentioning it now since I've seen it aplenty lately on these forums.
```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup0805
$ sudo dpkg-reconfigure xserver-xorg
```

---

