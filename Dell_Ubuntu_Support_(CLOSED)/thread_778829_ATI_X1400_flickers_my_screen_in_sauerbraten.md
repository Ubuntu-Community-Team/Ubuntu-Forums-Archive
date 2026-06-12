---
title: "ATI X1400 flickers my screen in sauerbraten"
date: 2008-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by alejobar on 2008-05-02
Hi there, I'm have a Dell Inspiron 6400 with a fresh install of Hardy and an ATI X1400, everything runs ok with compiz and the desktops effects, but when I run Sauerbraten the screen start to flicker, I can play the game for a while and then everything freeze. What can I do to solve this problem?

Thanks in advance for your help.

---

### Post by Bal_Zac on 2008-05-02
I had this problem using the open source driver on my old x850xt.  You might want to switch to the proprietary ati driver.  Also, try to disable compiz before playing, as it doesn't seem to play well with other 3d programs.

---

### Post by alejobar on 2008-05-02
I'm using the restricted driver for ATI, so I think is the correct one for my hardware, I will try disabling compiz before playing, do I just kill the compiz process?


****UPDATE**** 

Ok I kill all the compiz processes in System monitor and the game works perfect!!!!, so the question is, there's anyway I can disable/enable compiz easily? or can I change something in compiz manager in order to play without problems?

---

### Post by Cygoku on 2008-05-02
Yes there is a way to quickly enable/disable Compiz.  Some ppl would give you a command line but not me.  Here goes, since you are on Hardy Heron, you can search for an application called "icon fusion", this lets you to quickly enable/disable Compiz and/or Emerald.

Cygoku

---

### Post by Paul S on 2008-05-03
There's also a menu item for appearance that let's you select desktop effects.  It's a few mouse clicks to get to it, but it can do it.

---

### Post by esteckis on 2008-05-03
I am using The Heron version and if you want that Icon to enable or disable Compiz Fusion, it is in the synaptics download manager as a download listed as fusion-icon which is 

"tray icon to launch and manage Compiz Fusion"  I tried to do a search on my system first, and it was not there.

---

### Post by alejobar on 2008-05-05
> **Paul S said:**
> There's also a menu item for appearance that let's you select desktop effects.  It's a few mouse clicks to get to it, but it can do it.

Yes does what I'm doing, I go to preferences, appereance and change to no desktop effects and then I can play :guitar:

But when I activate the effects again I have to go to compiz manager to enable my custom effects and its kind of annoying :(

If someone know how to do it easily please help us!

---

### Post by |{urse on 2008-05-06
also i bet your video flickers when watching movies etc.

you can fix this with

> gstreamer-properties

click the video tab and select "X window system (no XV)" from the plugin: dropdown menu

NOTE: This isn't going to fix your sauerbraten from flickering, just uses the correct video overlay for gstreamer.

---

