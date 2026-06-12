---
title: "FireFox saving to network shares - SOLVED"
date: 2009-01-02
forum: General Help
---

### Post by bailey86 on 2009-01-02
Thought I'd post this up for others...

I have a Dell Inspiron 6400 Ubuntu pre-installed with 7.04 laptop.

Have upgraded twice to 8.04.

Saving from FireFox directly to a bookmarked network share was not possible - only local files were being shown.  Gedit was showning the shares fine though.

I then installed the gvfs-bin package, rebooted and recreated the network shares.

This means that the 'Save As...' dislog box now works OK from FireFox by showing the network shares.

Bear in mind you may need to have the firefox-3.0-gnome-support package installed - it was there by default in my setup.

Kev

---

### Post by dcstar on 2009-01-02
> **bailey86 said:**
> Thought I'd post this up for others...
.......
Saving from FireFox directly to a bookmarked network share was not possible - only local files were being shown.  Gedit was showning the shares fine though.

I then installed the gvfs-bin package, rebooted and recreated the network shares.

This means that the 'Save As...' dislog box now works OK from FireFox by showing the network shares.

Bear in mind you may need to have the firefox-3.0-gnome-support package installed - it was there by default in my setup.


Interesting, that seems the only GVFS package not installed by default.

BTW, this is also something that should actually be posted in the "Tips and Tutorials" sub-forum.

---

