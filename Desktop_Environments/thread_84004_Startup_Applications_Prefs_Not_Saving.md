---
title: "Startup Applications Prefs Not Saving"
date: 2005-10-30
forum: Desktop Environments
---

### Post by Spider-One on 2005-10-30
Hi,

I'd like to have a few apps start up with Gnome and it seems as though Gnome doesn't want to save my changes. I go System > Preferences > Sessions > Startup Programs and proceed to enter in the apps I wish to start with gnome. I've tried /usr/bin/***** and ***** but neither seem to work. I've tried an assortment of order numbers, but none work. I've tried running gnome-session-properties manually and seeing what I get in the terminal, but I get nothing. Any ideas?

---

### Post by Xian on 2005-10-30
That's odd. Let's try a very simple one and see if we can get that to work.
First install numlockx:

$ sudo apt-get install numlockx

Then place the word 'numlockx' in:
System > Preferences > Session > Startup Programs > Add

Now logout/login.
Your numlock on the keyboard shoule be auto-engaged.

What happened?

---

### Post by Spider-One on 2005-10-31
OK, so numlockx worked, but now I can't stop it from working. The numlockx option does not appear under System > Sessions > Startup Programs so I cannot delete it, is there any way to do this manually? Or a config file somewhere?

The main reason I'm trying to get this to work is because I'd like to have aMSN (preferred over GAIM, at least until 2.0.0) and gmail-notify start when I start gnome.

---

### Post by Spider-One on 2005-10-31
Bump

---

### Post by Spider-One on 2005-11-01
Bumpity buh-buh-buh-buuuuump

---

### Post by felix_stegerman on 2005-11-01
Hi,

The config files are: ~/.gnome2/session and ~/.gnome2/session-manual
If you delete them, the default session is restored.

You could also try to open the programs and use the "Save Session" option
to save a default session.


Felix

---

### Post by slux on 2005-11-01
I'd say numlockx is bound to stop if you uninstall the package. :P

---

### Post by Spider-One on 2005-11-01
Yeah it stops since I've uninstalled the package, but does nothing for helping my startup apps problem. I'd manually edit the config files, but don't know what format it would use. I might do a new install in a day or so, so maby see how it goes after that.

---

