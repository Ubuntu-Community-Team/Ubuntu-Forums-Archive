---
title: "Startx will not load Gnome or kde"
date: 2009-03-31
forum: Desktop Environments
---

### Post by WinterMadness on 2009-03-31
when i turn on my computer my OS loads into the terminal, and asks me to log in. I log in and type in startx, and this is what I get (along with a bunch of other things)

"failed to load nvidia kernel module"
***ABorting***
Screen(s) found, but none of them have a usable configuration.

this started happening  right after when I upgraded some things... (Hit mark all upgrades in synaptic)

I have three kernels to choose from, all of them do this

---

### Post by kerry_s on 2009-03-31
in that terminal type> sudo nano /etc/X11/xorg.conf

change the "nvidia" to "vesa" in the driver section, that should be enough to get you to gui, then you need to reinstall the nvidia driver.

---

