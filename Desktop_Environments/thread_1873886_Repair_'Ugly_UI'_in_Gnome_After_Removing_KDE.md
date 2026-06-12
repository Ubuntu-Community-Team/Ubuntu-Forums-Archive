---
title: "Repair 'Ugly UI' in Gnome After Removing KDE?"
date: 2011-11-02
forum: Desktop Environments
---

### Post by LiamMaru on 2011-11-02
So, I had to install KDE as it was listed as a requirement for a piece of software we've acquired at work, however after questioning the rationality of doing so, it turned out to be a miscommunication from the vendor - so, as a Gnome user, goodbye KDE.

However, after removing KDE, I notice the Gnome UI is significantly less 'pretty' and indeed usable as a result, than I remember it being:

[IMG]http://img69.imageshack.us/img69/1835/screenshotat20111102152.png[/IMG]

No folder icons, other things.

Is there some way I could 'repair' my system such that it would look like it did, before the KDE debacle? I could reinstall Ubuntu - this is a new machine and that is entirely possible - but I'd like to find another way to potentially save a bit of time, and hopefully learn a few things along the way.

---

### Post by cheat117 on 2011-11-02
I had to do something like this for myself after i took Macbuntu for a spin (If you are using macs or want to show up some mac users, do it) The best thing i learned to fix this with is to sudo apt-get autoremove gnome; sudo apt-get install gnome in the terminal and low and behold, it was fixed in a matter of seconds (Well minutes but yeah)

---

### Post by LiamMaru on 2011-11-02
Hmm, thanks cheat117, that seems to have done the trick, turns out I'll be reinstalling Ubuntu anyway, but aside from the grub screen and the login screen (which became debian-esque), it seems to have repaired most of my UI.

It also added a few new things (I noticed the debian package manager among other things), so I'd caution anyone else who tries this in future.

---

