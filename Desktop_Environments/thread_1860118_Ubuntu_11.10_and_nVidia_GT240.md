---
title: "Ubuntu 11.10 and nVidia GT240"
date: 2011-10-14
forum: Desktop Environments
---

### Post by whendidthishappen on 2011-10-14
I had 11.04 installed, and one day I turn on the machine and no longer see anything past the bootup.   I learned that its the video driver.  Something got updated, and screwed up the video driver. 
I install the latest nvidia drivers but still nothing.  I checked a million forums and could not find anything that worked.  I upgraded to 11.10, but Unity still didn't get fixed.

Can someone please walk me through fixing it.

I have nvidia gt240 which they I should be using GT240 driver.
Which version of the driver and how to fix it?

Can someone please walk me through this, as its been broken for months and I'm getting tired of Ubuntu breaking for absolutely no reason.

I will provide any necessary information.

---

### Post by philobyte on 2011-10-14
me too.  Same thing.  I had xinerama working with two screens in natty.  On Oneiric, cannot get the proprietary driver at all, and the open source looks odd, like it is 8 bit color or something, and only one out of two screens, and no openGL.


Not only that, natty had somehow become dependent on my configuration, so that on oneiric, the graphical login would fail... I tried moving .gconf, .gnome, .gnome2, out of the way, but could never log in at all.  Finally moved my home directory and created a new empty one, Then I could log in.

Installed on two other machines without issue, but on this one, total breakage. (some SATA controllers aren't recognized either) will be building launchpad items.

---

### Post by areeda on 2011-10-15
I have been working with a GT240 and GTX560 on 11.04. and the biggest gotcha I found is that you cannot mix the drivers from the repositories and nVididia.  The problem is they put libraries in different places and don't uninstall the other's libraries so you can end up with mixed versions of dynamic libraries.

IF you've loaded drivers from nVidia and the nvidia-common package, my suggestion would be to boot in recover mode, unistall both and then install the nvidia-common package.

I'm in the process of researching and trying 11.10 now so I don't have anything specific yet.

Joe

---

