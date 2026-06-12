---
title: "Why Doesn't ./configure, make, sudo make install Install Files to the System Anymore?"
date: 2009-02-26
forum: General Help
---

### Post by Mark76 on 2009-02-26
Way back in the day it did. But now it just does something in the untarred directory in your home folder.

That's not helpful at all.

---

### Post by taurus on 2009-02-26
I am not sure what you mean here.  Not all programs require you to run ./configure && make && sudo make install to build & install it.  If you have a specific program and/or problem, list it here.

---

### Post by Mark76 on 2009-02-26
Okay. As part of an experiment to see if I could make Xubuntu resemble a well-known proprietory operating system owned by some Californians I download the gnome-global menu bar plugin as a tar.gz. After detarring it to home folder I opened a terminal in the directory that was created and ran ./configure --without-gnome-panel (I wanted the xfce-panel plugin), then make and then sudo make install.  Naturally after this I expected to be able to add the plug in to my xcfe-panel, but it wasn't in the list. When I looked in the xfce4 panel plugins folder there was no globalmenu plugin at all.

---

### Post by mb_webguy on 2009-02-26
I'm assuming that there was a "configure" file in the folder, and that "make" and "sudo make install" ran correctly?

Try using [checkinstall]("https://help.ubuntu.com/community/CheckInstall").  Then you can look at the package in Synaptic to see what files were installed, and where.  It also makes uninstalling the software much easier.

---

### Post by sdennie on 2009-02-27
A lot of the time (most of the time?), ./configure will install in /usr/local/... unless you specify --prefix=/usr local.  I would check in /usr/local to see if your software installed there.  Though, as mentioned above, if you can get checkinstall to work, it's a much cleaner solution because it creates a .deb file and helps keep your machine more manageable.

---

