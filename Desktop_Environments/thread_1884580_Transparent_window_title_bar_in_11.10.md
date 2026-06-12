---
title: "Transparent window title bar in 11.10?"
date: 2011-11-21
forum: Desktop Environments
---

### Post by ticket on 2011-11-21
I recently loaded Knoppix 6.7.1 to do some admin work, and was impressed by its transparent window title bars. It was running the LXDE window manager.

I'd like to get the same for Ubuntu.  I could, I suppose, install lxde and boot that session, assuming it supports the transparency feature in Ubuntu.

But right now, I boot using the session "cairo-dock", which as far as I can tell uses the meta-city window manager (no gnome3 or unity for me!).

There used to be a setting in gonf-editor to modify the opacity of the window border for metacity, but that has now gone in 11.10.  Emerald is also gone in 11.10 - no longer supported.   And there doesn't appear to be anything in compiz settings either.

Anyone know how to achieve this?

---

### Post by buntudawg on 2011-11-21
Hi, 

Just checked my 11.10 (upgrade from 11.04, not clean install) installation and found the settings in my gconf-editor.

Open gconf-editor and navigate to: 

apps>gwd

There are settings for the opacity there, each a value ranging from 0 to 1 (0 fully transparent. 1 opaque).

Hope this helps.

---

### Post by jimmydean886-2 on 2011-11-21
I'm not sure about in GNOME/Cairo Dock, but if you install xubuntu-desktop and log in using that session, just check the control panel for XFCE, and those settings are right there.

---

### Post by ticket on 2011-11-23
Thank you buntudawg, 

> gconf-editor and navigate to: apps>gwd

does indeed work.  Can't figure out why I couldn't find that before!

Thank you also jimmydean886-2, nice to know XFCE supports this feature as well.

It's almost like getting a bit of emerald back!

---

### Post by buntudawg on 2011-11-23
No problem. Glad to be of assistance.

---

