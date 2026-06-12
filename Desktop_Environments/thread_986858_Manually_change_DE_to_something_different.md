---
title: "Manually change DE to something different?"
date: 2008-11-19
forum: Desktop Environments
---

### Post by MWP on 2008-11-19
Hi all,

Im running mythubuntu (Intrepid).

Current startup seq appears to be boot->xorg->gdm->gnome->mythtv.
I want change this to boot->xorg->gdm->mythtv so gnome isnt loaded at all.

Ive done this on a fedora box before, but cant remember how i did it.

What config files do i need to edit?

Thanks in advance.

---

### Post by ohzopants on 2008-11-20
gdm is gnome.

mythtv isn't actually a desktop environment, it's an application that just happens to run in full screen.

If you want to avoid running gnome because you want to minimize ressource usage you may want to consider installing xfce ([http://www.xfce.org/](http://www.xfce.org/)).  I've never done it myself but it should be as simple as installing the right package and selecting it from the login screen.

---

