---
title: "help reinstalling metacity"
date: 2008-01-27
forum: Desktop Environments
---

### Post by ispy on 2008-01-27
I installed enlightenment, and after a while decided i didn't want it anymore. so i went into synaptic (Still in enlightenment) and removed all the packages. upon logging out and back in, I can't get GTK Metacity to work, can someone help me out? this is driving me crazy. I have only a terminal with root access on my Ubuntu recovery. so if someone could guide me through this step by step, that would be much appreciated.

EDIT: I looked at the bottom of the error, and it says  /usr/bin/enlightenment cannot be found, so i'm guessing there's a file I need to edit somewhere.

---

### Post by benerivo on 2008-01-27
I would do```
sudo apt-get install enlightenment gnome-core
```which should reinstall both DE's, then you can uninstall enlightenment from within Gnome.

---

### Post by ispy on 2008-01-27
sweet, i love you man

---

