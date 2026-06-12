---
title: "XFCE - Error Adding Gnome"
date: 2008-03-06
forum: Desktop Environments
---

### Post by derekr44 on 2008-03-06
I'm currently running XFCE.  I'm attempting to install Gnome for my wife.  She likes the Gnome WM better than XFCE.  I'm basically setting up Gnome for her login and XCFE for mine.

Anyway... when attempting to install Gnome, it gave me package errors when trying to install Nautilus.  So I ran "sudo apt-get -f install" from the terminal to attempt to fix the packages.  Here is the error...

> (Reading database ... 140420 files and directories currently installed.)
Unpacking capplets-data (from .../capplets-data_1%3a2.20.1-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/capplets-data_1%3a2.20.1-0ubuntu1_all.deb (--unpack):
 trying to overwrite `/usr/share/applications/gnome-network-preferences.desktop', which is also in package gnome-network-preferences
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking gnome-control-center (from .../gnome-control-center_1%3a2.20.1-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/gnome-control-center_1%3a2.20.1-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/gnome-network-preferences', which is also in package gnome-network-preferences
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking gnome-utils (from .../gnome-utils_2.20.0.1-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/gnome-utils_2.20.0.1-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/share/applications/gnome-screenshot.desktop', which is also in package gnome-screenshot
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/capplets-data_1%3a2.20.1-0ubuntu1_all.deb
 /var/cache/apt/archives/gnome-control-center_1%3a2.20.1-0ubuntu1_i386.deb
 /var/cache/apt/archives/gnome-utils_2.20.0.1-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by kellemes on 2008-03-06
Have you tried removing these packages and reinstalling again?

---

### Post by derekr44 on 2008-03-06
> **kellemes said:**
> Have you tried removing these packages and reinstalling again?

Yes I have.  The install always fails at the same spot.  I don't know if it is installing the packages out of order or what.

I'm only installing "gnome" from Synaptic Package Manager.  It is automatically including several other packages along with it because of dependencies.  Could some of those dependencies be broken?

---

### Post by derekr44 on 2008-03-06
Anybody?  I even get the errors when I use:
> sudo apt-get install gnome

All I'm trying to do is install Gnome...

---

### Post by derekr44 on 2008-03-11
...

---

