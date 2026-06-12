---
title: "Kubuntu + Avant window navigator dependency"
date: 2007-07-16
forum: Desktop Effects &amp; Customization
---

### Post by sdlvx on 2007-07-16
Alright, I searched, and I couldn't find anything.  I know this is probably an easy fix.

I have Kubuntu 7.04 installed, with Compiz Fusion, and of course, Avant Window Navigator.

When I first started AWN, it would run, but it wouldn't open up the preferences, or applets or launchers.

I fixed the Preferences by installing missing dependencies (I ran AWN in a terminal, and checked the output).

However, I still can not get the applets and the launchers window to open up, because it says I am missing "gnomedesktop".

However, when i do

sudo aptitude install gnomedesktop

iit tells me that that package does not exist.  Am I missing a repo or something, or is there another package that I have to install?

Thanks for your help.

---

### Post by bronze on 2007-07-16
I don't really have a solution for your problem, but in case you're wondering, the reason why you can't use AWN as intended (most likely) is because it's written for gnome, which is the desktop environment used in Ubuntu. Try searching for "gnome desktop" , "gnomedesktop" and "gnome-desktop" in synaptic, and you might be able to download the dependencies, but this will also install the gnome desktop environment.

---

### Post by hyperair on 2007-07-17
Try using the debs from Trevino's eyecandy repository: [http://downloads.tuxfamily.org/3v1deb](http://downloads.tuxfamily.org/3v1deb). Those resolve the dependencies for you I reckon.

In case this helps, these are the dependencies listed by "apt-cache depends avant-window-navigator-svn"
```
hyperair@Hyperair-PC:~$ apt-cache depends avant-window-navigator-svn
avant-window-navigator-svn
  Depends: libart-2.0-2
  Depends: libatk1.0-0
  Depends: libawn-svn
  Depends: libbonobo2-0
  Depends: libbonoboui2-0
  Depends: libc6
  Depends: libcairo2
  Depends: libdbus-1-3
  Depends: libdbus-glib-1-2
  Depends: libfontconfig1
  Depends: libgconf2-4
  Depends: libglade2-0
  Depends: libglib2.0-0
  Depends: libgnome-desktop-2
  Depends: libgnome-keyring0
  Depends: libgnome2-0
  Depends: libgnomecanvas2-0
  Depends: libgnomeui-0
  Depends: libgnomevfs2-0
  Depends: libgtk2.0-0
  Depends: libice6
  Depends: liborbit2
  Depends: libpango1.0-0
  Depends: libpopt0
  Depends: libsm6
  Depends: libstartup-notification0
  Depends: libwnck18
  Depends: libx11-6
  Depends: libxcomposite1
  Depends: libxcursor1
  Depends: libxdamage1
  Depends: libxext6
  Depends: libxfixes3
  Depends: libxi6
  Depends: libxinerama1
  Depends: libxml2
  Depends: libxrandr2
  Depends: libxrender1
  Depends: gconf2
  Depends: libawn-svn
  Depends: libgnomevfs2-0
  Depends: libgnome-desktop-2
  Depends: libgnome2-0
  Depends: libwnck-common
  Depends: python-gtk2
  Depends: libgconf2-4
  Depends: libglib2.0-0
  Depends: python-gconf
  Depends: libxdamage1
  Depends: libxcomposite1
  Recommends: beryl
  Recommends: compiz
  Conflicts: avant-window-navigator
hyperair@Hyperair-PC:~$ 

```
I reckon that if you install the packages listed as "depends" it'll fix the problem.

---

### Post by sdlvx on 2007-07-18
I appreciate the help, but the packages wouldn't install, I think they are already installed.

I am just configuring avant with gconf-editor now.  It works, and plus, I can enable refletions and stuff.  It looks nice.

---

### Post by hyperair on 2007-07-18
Good to hear.

---

