---
title: "gnome-panel Installation Question"
date: 2012-05-27
forum: Desktop Environments
---

### Post by Lucradia on 2012-05-27
If I install gnome-panel ONLY via the mini.iso, will it also install all of the GNOME Shell / GNOME 3.0 stuff? Or will I have just gnome classic?

I really hope I only get gnome classic. As I don't want to use GDM or something to switch to gnome classic. (As I don't want a DM)

---

### Post by LarsKongo on 2012-05-28
If you want a minimal Gnome classic desktop, install with the following command:

*sudo apt-get --no-install-recommends install gnome-session-fallback*

It will just install the stuff that requires the Gnome session to work. (Including gnome-panel, gtk3 and a bunch of other stuff.) It won't install Nautilus, gnome-control-center, gnome-themes-standard or any icons etc.

Then use *startx* and see if it works. Keep using *sudo apt-get --no-install-recommends install package-name* to avoid adding any extra stuff that you don't need.

I haven't tried that install with just "gnome-panel", so I'm not sure which dependencies it will add. But it certainly won't add gnome-shell or gdm which you're worried about. But I'm not entirely sure it will add any fallback session either. It may just install itself so it can be used as a modular panel on any type of x-session.

---

