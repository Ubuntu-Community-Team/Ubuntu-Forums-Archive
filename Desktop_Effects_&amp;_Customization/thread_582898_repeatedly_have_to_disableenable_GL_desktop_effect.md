---
title: "repeatedly have to disable/enable GL desktop effects"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by dougleduck on 2007-10-20
I've installed the compizconfig package, but after changes are made to any settings, even as simple as changing the number of faces on the cube I have to disable/enable desktop efffects in GL desktop.

Also when changing settings many of the others seem to reset to defaults. Any ideas?

I upgraded from feisty to gutsy yesterday.

Also when I start GL desktop I have to try to open it twice, but only one window opens initially (once ive disabled and enabled desktop effects another appears).

---

### Post by dougleduck on 2007-10-21
Someone must have an idea...

---

### Post by Rob500 on 2007-10-21
The same thing happened to me yesterday, it was a real headache and the screen kept flickering on startup so I just thought sack it, did a clean install of Feisty, installed Compiz Fusion and upgraded to Gutsy, now I can enable/disable it using the run command.

---

### Post by dougleduck on 2007-10-21
Just reinstalled compiz-fusion and related packages.

When starting gnome-compiz-preferences to turn on desktop effects I get the output from terminal (still have to run the command twice.

(gnome-compiz-preferences:17869): libgnomevfs-CRITICAL **: gnome_vfs_get_uri_from_local_path: assertion `g_path_is_absolute (local_full_path)' failed

** (gnome-compiz-preferences:17869): WARNING **: plugin inputzoom isn't installed

still having same problem as before

---

### Post by Rob500 on 2007-10-21
Do you want all of the effects or just some of the basic ones?

---

### Post by dougleduck on 2007-10-21
Well I dont *need* any of them; I wanted to play. Some of them seemed useful though. If I could get it to actually change the setting without having to turn the effects on and off everytime that'd be great.

---

### Post by dougleduck on 2007-10-23
bump

---

### Post by ljp37 on 2007-10-25
(bump)

This exact same thing happens to me, also after upgrading from Feisty to Gutsy.

I have to keep fighting with the settings, and now it seems I can't get more than one workspace going no matter what I try (although it was working nicely with the wall effect yesterday)...

I've been using "compiz --replace" to restart compiz after making changes.  Sometimes they take, sometimes not.

Back to metacity.  Sigh.

---

### Post by dougleduck on 2007-10-25
It seems to be working better now. I've uninstalled gnome-compiz-manager as this seemed far more trouble than its worth. I still have to use compiz --replace too sometimes but more often than not it updates automatically.

I've uninstalled and reinstalled many times, and its not perfect but closer (I'm having a few issues with some of the features but I think they warrant a separate post).

Where's the technical support dissapeared when  you need it?

---

