---
title: "Make KDE fonts go away."
date: 2006-01-29
forum: Desktop Environments
---

### Post by DrSturgeon on 2006-01-29
So every little once in a while I have this odd idea that I want to use KDE for a while.  I install it, use it for 15 minutes, remember all the reasons I hate KDE, and switch back to Gnome.

I just finished one such escapade, and now that I'm done cleaning out everything on my system that has a ridiculously glossy icon, there's still one problem.

I cannot make the fonts pay attention to the Gnome Font Preferences.  Or, at least some of them.  Anything that should respond to the "Application Font" preference still looks likes it's being drawn by the gtk2 QT engine, which yes, I did uninstall.

There is no trace of anything on my system that should be overriding that font setting, and I can't figure it out.

I guess in the grand scheme of things, this isn't that big of a problem, but it's really bugging me.  Any ideas?

---

### Post by zoryn on 2006-03-03
not to awaken a dead thread, but i have the exact same problem... any clues?

---

### Post by ShanghaiTeej on 2006-03-06
I have the same problem and am not installing kde anymore beause of it.  I did find a solution on these forums that said you should switch from using gtk-fonts to whatever KDE uses in the controls panels in KDE.

---

### Post by DrFunkenstein on 2006-03-06
Did you guys try to delete ~/.gtk-qt-rc (or something like this).
You could also try to delete all the kde settings my removing ~/.kde and see if that fixes the problem.

---

### Post by ComplexNumber on 2006-03-06
gnome has better capabilities for font rendering.  thats why fonts tend tio look nicer in gnome.

**DrSturgeon**
sounds like another case of kde trying to take over the whole system ;). how much of kde have you got rid of? if kde is still there, then the system still thinks that kde is now default, so gtk will look at the gtk-qt configuration to get the info about fonts and themes etc. even though you uninstalled the gtk-qt engine, that does _not_ remove the configuration files that stay in your home directory. you need to make a copy of these and then delete the directory.

---

### Post by simsalabim on 2006-03-13
[QUOTE=DrFunkenstein]Did you guys try to delete ~/.gtk-qt-rc (or something like this).
You could also try to delete all the kde settings my removing ~/.kde and see if that fixes the problem.[/QUOTE]
I think this solved the problem for me. I'm not sure of the exact files names of the files I deleted. Something gtk and kde related anyway...

---

