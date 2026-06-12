---
title: "Removing features from GNOME"
date: 2008-02-17
forum: Desktop Environments
---

### Post by armitage1337 on 2008-02-17
Hi,

I set up GNOME for some non-tech savvy users, and they keep messing up the GUI on accident. Is there any way to "remove" features from the GNOME GUI? The main things that I'd like to remove are (1) allowing the panels to be moved and (2) changing the size of the text in Nautilus. Any ideas?

Thanks!

---

### Post by sajro on 2008-02-17
This is quite obviously not the smartest or easiest way, but a way nonetheless. You could recompile GNOME sans those 'features (or the individual components of it), make a deb via checkinstall or whatever, uninstall GNOME or those components, and use your .deb to set up.

---

### Post by erfahren on 2008-02-17
you could try going through the gnome-configuration-editor and see what options you can change or disable.launch it with the command: "gconf-editor"

---

### Post by armitage1337 on 2008-02-17
Hmm, I'll take a look at that. I'm not too familiar with GNOME though. I set it up for non-tech savvy people because it wouldn't have enough features to cause problems, and now they're messing up GUI stuff with no idea whats going on :confused:

---

### Post by julian67 on 2008-02-17
A good approach would be to read [Desktop Administrators' Guide to GNOME Lockdown and Preconfiguration](http://library.gnome.org/admin/deployment-guide/) and also check out [Pessulus](http://www.gnomefiles.org/app.php?soft_id=1082) > pessulus is a lockdown editor for GNOME, written in python.
 
pessulus enables administrators to set mandatory settings in GConf. The users can not change these settings.

Use of pessulus can be useful on computers that are open to use by everyone, e.g. in an internet cafe.

It might even be part of Gnome now, I'm not sure as I'm using Xfce

---

### Post by armitage1337 on 2008-02-18
> **julian67 said:**
> A good approach would be to read [Desktop Administrators' Guide to GNOME Lockdown and Preconfiguration](http://library.gnome.org/admin/deployment-guide/) and also check out [Pessulus](http://www.gnomefiles.org/app.php?soft_id=1082) 

It might even be part of Gnome now, I'm not sure as I'm using Xfce

This seems like what I need - thanks a lot!

---

