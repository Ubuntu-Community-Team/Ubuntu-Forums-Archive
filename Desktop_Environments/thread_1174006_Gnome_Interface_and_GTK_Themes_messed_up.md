---
title: "Gnome Interface and GTK Themes messed up"
date: 2009-05-30
forum: Desktop Environments
---

### Post by Sigurd Suhm on 2009-05-30
Hey fellow Ubuntu lovers. I hit a kinda strange and annoying problem today. I think I was running a deborphan when suddenly my Gtk Themes looked different. For example the Clearlooks theme has plain white background for the menu and the Human theme is missing the progress bar and such.
Also my GnomePanel looks somewhat different. More Win 95 style if you know what I'm getting at. I've been unable to figure out what could have caused all of this so far. At first all my themes disappeared from the Appearance settings menu but I managed to get those back. Since then I've been toying around with installing Gtk Engines, reinstalling ubuntu-artwork, ubuntu-desktop and gnome-desktop-environment and such but to no avail. Any input on this is greatly appreciated.

Thanks in advance
Regards
Sigurd

---

### Post by maybeway36 on 2009-05-30
That sort of thing usually happens when GTK can't find the right theme. The only thing I can think of is to reinstall gtk2-engines, then try the Clearlooks theme again.

---

### Post by Sigurd Suhm on 2009-05-30
I had already reinstalled gtk2-engines... Several times I think actually. :P

And now after spending most of the day looking at it and completely neglecting my girlfriend I managed to get Clearlooks back to normal by compiling and installing the engine seperately.

---

