---
title: "[SOLVED] Can I deactivate one screensaver ?"
date: 2008-05-25
forum: Desktop Environments
---

### Post by Kevbert on 2008-05-25
I'm running Ubuntu 7.10 x64 on an AMD2 with 4Gb ram and nVidia Geforce 7600 GS (512Mb).  I normally run BOINC (Seti etc) and Compiz in the background.
I've downloaded the extra screensavers (xscreensaver-gl-extra) via Synaptic.
If I choose the random screensaver option there's one screensaver that causes me a problem - Braid.  Is it possible to disable this single screensaver ? (as it's part of a package ?)
If Braid runs the PC locks up solid, meaning a visit to Mr Reset button.  It  will even lock up if I perform a preview, but if I turn off BOINC it works fine.

---

### Post by sdennie on 2008-05-25
You should be able to.  There are two possible solutions in the following thread: [http://ubuntuforums.org/showthread.php?t=806364](http://ubuntuforums.org/showthread.php?t=806364)

---

### Post by Kevbert on 2008-05-25
Thanks for that.  It works like a charm.  Is there a good guide on what you can do with gconf-editor ?  It seems like it's a powerful tool that could be very useful.

---

### Post by sdennie on 2008-05-25
I've not really looked for one.  Really it's just a specialized XML editor (it's similarities to regedit on Windows end at the layout of the UI).  Everything lives in corresponding .xml files in ~/.gconf and most of the options are fairly well documented within the editor.  Having said that, there are usually ways to configure an app without using gconf-editor.  It's mostly for options that aren't presented in the purposely minimalistic options that gnome usually provides for apps that are generally suitable for most users.

---

