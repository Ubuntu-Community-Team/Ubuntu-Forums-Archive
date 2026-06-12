---
title: "Desktop Problems (no right-click menu)"
date: 2006-08-26
forum: Desktop Environments
---

### Post by wired465 on 2006-08-26
I was messing with some settings and i checked/unchecked "show_desktop" in gconf->apps->nautilus->preferences and now i can't see any icons on my desktop nor can i right click on the desktop. Please save me! :confused:

---

### Post by max_dingemans on 2006-08-26
Did you try restarting X (by pressing Ctrl+alt+backspace)?  (Assuming anything that needs to be saved, is saved?)

---

### Post by wired465 on 2006-08-26
yes I did. my session now starts without a desktop background and without the ability to right-click the desktop.

---

### Post by wired465 on 2006-08-28
/bump
i can create a new user to get the desktop menu back but my icons are still missing :( Anyone offer any advice?

---

### Post by cptnapalm on 2006-08-28
This is easy.  Have no fear.  What is happening is that your configuration basically told nautilus not to draw the desktop.  When Nautilus is set to do so, it draws the icons and takes care of right clicks.  That last bit is damn stupid, but anyway...

If you can get back to that same spot in gconf, then just change that same setting back.  (I hate gconf, not that you asked).  If you can't there is a package called gtweakui, so...

apt-get install gtweakui

(it might be in a *verse repository)

Head up to the system menu, click it, then click Preferences, then gTweakUI - Nautilus

Make sure 'Use nautilus to draw desktop' is selected as well as whatever else there you want.

Should be good to go.

---

### Post by Noffie on 2006-08-29
Hey, could you please let us know if this solution works?

I had a very similar problem and was forced to reinstall gnome with a ```
aptitude purge gnome gnome-desktop-environment
``` then I had to go through and delete a bunch of .gconf and .gnome and .gnome2 stuff in my home direcory.  Basically I had to attempt to completely remove gnome and all it's settings, then reinstall it.

It would be greate if the simple nautilus solution posted above worked! :D

---

### Post by razputinoleander on 2008-02-07
It does indeed work.
gconf-editor is one of the worst Linux tools I've ever used.  gtweakui is a much better replacement for it.

I ran gtweakui-nautilus and was able to restore the desktop.  However; icons are now visible on the desktop.
I'd like to be able to disable desktop icons but still have right-click desktop menus, a.k.a Xfce.

---

