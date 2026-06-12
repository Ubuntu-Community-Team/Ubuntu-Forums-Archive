---
title: "Ubuntu to Ubuntu-Mate"
date: 2019-05-08
forum: Desktop Environments
---

### Post by josaphat2 on 2019-05-08
I've successfully converted Ubuntu to Ubuntu-Mate

I'm a bit rusty so I did this within the default Ubuntu's Gnome3 shell. I don't know how to switch to CLI anymore in 18.04. Ctrl+alt+Fx did nothing.

Anyway what I did was just

[B]apt-get purge gnome* gtk*

apt-get autoremove --purge[/B]

then

**apt-get install ubuntu-mate-desktop**

Ubuntu will reinstall any required gnome and gtk libraries app automatically, and plymouth splash screen will also change to ubuntu mate.

Don't get lock out from gnome shell, if you do, just reboot and you'll need to login CLI/bash. You can proceed from there.

If you do finished all the process above within Gnome UI, after you reboot your desktop will automatically switched to Mate and no trace of Gnome 3 at all.

Probably not a good idea, but for daily light desktop use, this will do.

Why? I read an article that test all the available desktop environments. Forgot which article that is. Performance and efficiency wise, Mate is the winner, even compared to the low footprint DE such as XFCE and LXDE.

Besides I started to learn Linux in Gnome 2 era and fell in love with it instantly, even though KDE was recommended by most because of its sheer customizations options.

---

