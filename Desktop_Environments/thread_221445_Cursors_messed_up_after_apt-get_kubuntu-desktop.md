---
title: "Cursors messed up after apt-get kubuntu-desktop"
date: 2006-07-23
forum: Desktop Environments
---

### Post by eXecu7or on 2006-07-23
I've installed 6.06 a couple of days ago and yesterday I've decided to add the kubuntu-desktop package. However, it seems to have messed up the mouse cursors.

On the login window it appears black and with no shadow (I'm a sucker for eye candy! :) than it changes to the default human theme. But still, even in gnome there are instances where the old style black cursors appear (during background operations, for example). I've tried setting a theme using System->Preferences->Mouse, but to no effect.

Is there another way to set a global xorg cursor theme?

Thank you in advance for your answers.

---

### Post by ciscosurfer on 2006-07-23
The kubuntu-desktop package effectively overwrites your ubuntu-desktop package.  To get back your cursors and themes, try reinstalling the ubuntu-artwork package.```
sudo aptitude install ubuntu-artwork
```

---

### Post by eXecu7or on 2006-07-24
Nop, it didn't do the trick... However, after installing some xcursor package in Synaptic, it changed the black cursor scheme from gdm to another black cursor scheme, even uglier... Is there any way to set a X global cursor theme?

---

### Post by jclmusic on 2006-12-09
i think it's a text file somewhere in /usr/share. i'm trying to find it myself, but with no luck yet, so BUMP! :p

---

