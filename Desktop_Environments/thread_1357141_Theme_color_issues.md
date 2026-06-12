---
title: "Theme color issues"
date: 2009-12-16
forum: Desktop Environments
---

### Post by aditya2507 on 2009-12-16
Hi,

I had been toying around with Ubuntu themes -- installed a few extra from the rep and also installed the Gtk theme changer. What happened is that now when I change the theme (from Appearance Preferences) I colors of the window borders (and other frames, I think) do not change while everything else does. Its basically set at Human-clearlooks right now. So if I choose the theme "clearlooks" or "glossy" the window borders are set at the same color as human-clearlooks and don't turn Blue.

I have tried to reset the whole thing by deleting the .gnome2 and other directories but it doesnt work.

Please help!

Aditya

---

### Post by aditya2507 on 2009-12-16
Ok, I resolved this on my own. So I am posting the answer if someone ever needs it -- All I did was delete the .gtkrc directories from my home directory. Here is the exact command:

rm -rf .gtkrc-2.0 .gtkrc.bak

Hope it helps!

- A

:guitar:

---

