---
title: "X11 Forwarding and Fluxbox"
date: 2006-06-20
forum: Desktop Environments
---

### Post by colonel_panic414 on 2006-06-20
Recently, I have been searching for an alternative to using VNC and SSH to gain secure remote access to my desktop, as VNC is rather slow, as it has to refresh the screen for each change. Someone suggested I try the X11 forwarding feature of PuTTY, since I am usually connecting from a Windows machine at work. Well, using a portable Win32 X server, Xming, I was able to load up my apps comparatively quicker than through VNC. 

I also wanted to have some sort of graphical environment to work  with, because I prefer Fluxbox and Gnome to Windows' GUI, but I couldn't quite get it to work. Gnome doesn't work because, for starters, it's already running back at home, so I tried Fluxbox, which did actually load up in my portable Xserver. I grabbed the four packages from Synaptic, fluxbox, fbdesk, fbpager, and fluxconf. My problem with fluxbox is that I do not have any idea how to add a menu to it. All of them are blank. I tried using the menu editor utility, but strangely, it will not work. Everytime I try to add something, it gives me a message similar to this: ```
(fluxmenu:14864): Gtk-CRITICAL **: gtk_tree_store_append: assertion `VALID_ITER (parent, tree_store)' failed
``` and doesn't do anything.

One more thing, I also tried XFCE, and tried to forward it. It doesn't work coming through the connection. It complains about extensions. If I can find the error message it gave me, I'll post it as well.

Sorry for the long post, and if anyone has any helpful tips about fluxbox menus or X11 forwarding, I would appreciate any and all help! Thanks!

---

