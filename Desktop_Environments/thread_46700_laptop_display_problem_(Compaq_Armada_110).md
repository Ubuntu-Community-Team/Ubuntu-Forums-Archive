---
title: "laptop display problem (Compaq Armada 110)"
date: 2005-07-05
forum: Desktop Environments
---

### Post by lonboy on 2005-07-05
Hello. I am having some problems with my laptop display and have had a similar issue under FC3, Debian-Woody and Gentoo. All running Gnome.

The problem:

The image resolution is correct,  but the image is off center (slightly shifted right about 2 mm). This leaves 2 mm of dead (black) space on the left, which the pointer cannot access and 2 mm of lost space on the right, where the pointer disappears.  Is there a way to correct this? I was never able to figure out how to fix this problem in any of the previously mentioned distros.

Video card: Trident Cyberblade i7 (currently using generic Trident driver)

I used Linspire once and that has been the only distro I have found that did not have this problem, but I can't bring myself to use it.

---

### Post by darkmatter on 2005-07-05
You could try changing the refresh rate (a quick google of you laptops specs suggests a refresh of 60Hz). If that doesn't help, you could try manually changing the screen position (had a similar problem with my desktop. Turned out that someone had been messing with my ***monitors*** setting, and had nothing to do with Ubuntu itself)

Also, check that the specs listed in /etc/X11/xorg.conf match those in the specs for you laptops display. If they don't then:

$ sudo gedit /etc/X11/xorg.conf

:and enter the appropriate values. Then save the changes and restart X (Ctrl+Alt+Backspace)

---

