---
title: "Gnome Panel Repeatedly Freezes, System generally unstable."
date: 2008-09-10
forum: Desktop Environments
---

### Post by benpage26 on 2008-09-10
Hi guys,

I'm looking for some advice on how I can debug and find out what the problem is that is causing my computer to be unstable.  As I type, my Gnome Panels (ie, the top and bottom of my desktop with the Applications | places ... menus) does not respond to clicks.  I can still use firefox and switch workspaces and windows with the keyboard shortcuts.  Also, unsure if this is related or not, but my pidgin and firefox sometimes randomly freeze (yesterday even Gnome Terminal would stop responding as soon as it was loaded).  Can anyone advise me on how to track down the problem?

I have run pidgin from the terminal to see the output, but then Pidgin crashed and brought the terminal down with it.  So i cannot get the error message (I believe it was related to object disposal)

---

### Post by phidia on 2008-09-10
From the System menu System>Administration>System Log you can read through those to see if there are errors/messages there related to the freezing-lockups.

When the freezing happens you can also try opening a tty (another access to the system) by pressing the Alt+Ctrl+F1 keys if that does open up a commandline for you you can type "dmesg" and copy & paste that output here.

Please provide the system specs and the version of Ubuntu you are using.

---

