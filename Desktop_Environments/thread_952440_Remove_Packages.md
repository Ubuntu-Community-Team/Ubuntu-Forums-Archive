---
title: "Remove Packages"
date: 2008-10-19
forum: Desktop Environments
---

### Post by andy_t on 2008-10-19
Hi,

I've just done a fresh install of 8.04 and was removing packages that I don't need, several of the ones I wanted to remove were linked to ubuntu-minimal and ubuntu-desktop... is it ok to remove these packages or will I run into issues later.

Also on an unrelated note, I saw an article a week or so ago about an app that does the same as vLite does for Vista but for ubuntu, anyone know the name?

Cheers!

---

### Post by Bucky Ball on 2008-10-19
Not sure about ubuntu-minimal but don't remove desktop! If you are in Synaptics have a good look at what it is you're taking out. In a terminal, you could put:
[B]
sudo apt-get autoremove[/B]

and that should get rid of anything unused.

---

### Post by andy_t on 2008-10-19
It's just I want to ditch the printing packages and a few others, most seem to be linked to desktop or minimal... I don't need the screensaver packages but try to remove and the system wants to get rid of a ton of other stuff!

---

### Post by Bucky Ball on 2008-10-19
I just went to Synaptics and I have gnome-screensaver and eternity-screensaver installed. I can't see there would be a problem removing either. You have the option to remove or completely uninstall so maybe experiment. If there is a problem, you can always re-install, as long as you keep track of what you have dumped.

Do a search in Synaptics for 'print' and see what you come up with there also. Again, if it is only the cupsys-driver-Gutenberg you could remove, as long as you are not intending to do any printing that is.

---

