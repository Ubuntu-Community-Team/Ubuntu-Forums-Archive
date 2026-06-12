---
title: "xubuntu gtk-engine pixmap install"
date: 2006-06-27
forum: Desktop Environments
---

### Post by mättu on 2006-06-27
In ubuntu breezy i used "milk 2.0" as my desktop-theme. It uses the gtk-engine "pixmap".

Now in xubuntu there is no such engine preinstalled, which makes Milk (and other pixmap-based-themes) looking weird.

Install of "pixmap" with synaptic installed the engine in 
/usr/lib/gtk/themes/engines
and not
/usr/lib/gtk-2.0/2.4.0/engines 
where the others reside.

Copying of pixmap to the standard directory did not help.

Help much appreciated

:m)

---

### Post by mättu on 2006-06-28
o.k. 
installed 
gtk-engines-xenophilia
which installs itself correctly and puts many themes in /usr/share/themes

But none of them becomes listed in the settings manager -> user interface.

Bug?

---

### Post by mättu on 2006-09-01
hello posters ;-)

I'm back with a workaround.
Just install gnome-themes..
This installs some enginges and seems to do things behind the scenes which get things working smoothly.
I'm sorry I can't help with a cleaner solution, because I lack of time & knowledge. Anyway:

One more very happy xubuntu-user 
:m)

---

