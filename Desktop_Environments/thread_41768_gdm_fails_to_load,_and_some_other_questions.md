---
title: "gdm fails to load, and some other questions"
date: 2005-06-14
forum: Desktop Environments
---

### Post by Moonbuzz on 2005-06-14
Hello to all.

I first want to say, that this is the first time I've installed any distribution of Linux on one of my PCs, and I'm quite glad that it's Ubuntu, as it really sucked me in, rather than deterred me from using Linux.

As for my question(s):

First, I have a problem with the system not booting up gdm. Once it boots up, it gives me the console screen. I log in, then type sudo gdm, and everything goes back to normal. I originally installed Gnome Ubuntu, then installed KDE over it (for comparison), then uninstalled KDE for Gnome again, I think that the uninstallation of KDM must have left a black hole where the boot manager tries to load a desktop manager. Any ideas?

TIA.

Erez

---

### Post by Knome_fan on 2005-06-14
Hm, not many ideas, but anyway: 

1. Make sure that the default display manager in /etc/X11/default-display-manager is actually /usr/bin/gdm. (Maybe it somehow was changed to kdm when you played with KDE).
2. Make sure ubuntu-desktop is installed, as this should install all the "normal" ubuntu packages.

Good luck!

---

### Post by Moonbuzz on 2005-10-04
Forgot to mention, but it worked :)

---

### Post by blair on 2005-12-09
I had a similar problem. I upgraded from 5.04 hoary to 5.10 breezy and after completing the update, my system would only boot to the login prompt. The desktop did not load. I checked Synaptic and found that the ubuntu-desktop package was missing. I installed the package, restarted the machine and everything worked perfectly. Thanks for the tip.

---

