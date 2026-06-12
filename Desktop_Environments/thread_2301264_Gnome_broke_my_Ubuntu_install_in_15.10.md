---
title: "Gnome broke my Ubuntu install in 15.10"
date: 2015-11-01
forum: Desktop Environments
---

### Post by lwfx on 2015-11-01
So, I just wanted to check out the gnome desktop and used [B]sudo apt-get install ubuntu-gnome-desktop
[/B]Looked around for a bit and was done, logged into my Unity area and the cursor is black and my wallpaper is gone. No right click menu and just generally a mess. I remove the Ubuntu-gnome-desktop with purge, but still the same thing. Followed some
advice given on some other forums to fully remove gnome and reinstate Unity to no avail. I tried 3-4 different methods, so I couldn't tell you EXACTLY what I last did. Involved more purges and autoremoves, etc. Any advice? Would just like my old Unity back.&#8203;

---

### Post by dellboy56 on 2015-11-01
Hi there let me try and help you! [COLOR=#111111][FONT=Ubuntu]Login into virtual console (ctrl+alt+F1) during the black screen appears,then run the below commands,[/FONT][/COLOR]sudo apt-get install ubuntu-desktop
sudo apt-get install unity 

if that doesn't work let me know and I'll help you in a another way by the way so you completely removed unity and the Ubuntu desktop if so use those commands in the terminal

If you did switch to gnome log out and there is a little gear on the login screen it should display unity unity 2d and gnome desktop

---

### Post by lwfx on 2015-11-01
I used those commands but that didn't work. Tried the --reinstall modifier to force reinstall (I think that's the one) too.
It's oddly enough still showing gnome and gnome-classic as options even though it says gnome isn't installed x_x

---

### Post by dellboy56 on 2015-11-01
Hmm I'm not sure you might want to ask the IRC community if they could help you &#55357;&#56841; Good luck and hope your distro is useable again

---

### Post by grahammechanical on 2015-11-01
Be careful what "gnome" you remove as Ubuntu uses the Gnome 3 desktop environment. You should have installed the Gnome 3 shell or Gnome shell as it is called in the Ubuntu Software Centre.

[https://wiki.gnome.org/Projects/GnomeShell](https://wiki.gnome.org/Projects/GnomeShell)

ubuntu-gnome-desktop is a meta package. Removing it does not remove all the packages and applications that were downloaded and installed through the ubuntu-gnome-desktop meta package.

[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

Consider the easy fix - reinstall.

---

