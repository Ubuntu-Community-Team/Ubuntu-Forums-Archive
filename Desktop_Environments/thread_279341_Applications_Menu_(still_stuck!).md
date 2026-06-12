---
title: "Applications Menu (still stuck!)"
date: 2006-10-17
forum: Desktop Environments
---

### Post by gavlees on 2006-10-17
Hi!

I'm fairly new to Linux and Ubuntu and have come across my first problem today.  I have been trying to set up Ubuntu for audio/music work and was following the instructions here:

[http://wiki.ubuntustudio.org/index.php?title=Studio_Preparation]("http://wiki.ubuntustudio.org/index.php?title=Studio_Preparation")

I then tried to run ZynAddSubFx while having Jack and Virtual Keyboard open and the system froze.  I have no idea how to attempt to recover from this (ie, what the Linux equivalent of ctrl-alt-del is) so simply turned off my laptop.

Rebooted - got the disk-check message and rebooted again.  Upon system start-up, I found that the applications menu was not working (no drop down, save for a 4x4 pixel box,) so I hit these forums.

I have tried
> sudo apt-get install menu
dpkg-reconfigure menu gnome-menus menu-xdg
and
> apt-get install menu-xdg
and
> killall gam_server
and just about every other solution that has been offered, but still to no avail.

Can anyone help?  I did consider upgrading to Edgy, but was wary of what a beta release might do to an already unstable OS.

Many thanks in advance,
gav./

---

### Post by CatKiller on 2006-10-17
Crikey - installing a new Operating System because the menu's broken seems a bit extreme. I've not come across your particular problem before, but have you tried removing the menu from the panel and putting it back again? It's just a panel item like the clock and whatnot. Or, if that doesn't help, you could try creating a new account to see if it's just your account that's broken.

---

