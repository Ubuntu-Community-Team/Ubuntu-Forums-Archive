---
title: "Eliminate a single package"
date: 2005-03-15
forum: Desktop Environments
---

### Post by mirtux on 2005-03-15
Hi,
  i have one question regarding the dependecies of programs. I would like to wipe out gnome-gv (ggv) from my box since i can work quite easily with Evince, Acrobat reader and gv. But when i try to remove ggv from my system with synaptic it tells me that it want to remove the entire gnome and gnome-desktop-environment. How is possible to do it without breaking the system?

Thanks,
MC

---

### Post by IdoMcFly on 2005-03-15
I have the same need with a localization package of firefox : I want it in english but all the other apps in French, but I can't remove the firefox package alone

---

### Post by az on 2005-03-15
Only empty (meta) packages will be removed.  Do not worry.

---

### Post by mirtux on 2005-03-15
Hi azz,
  you are referring to my post or to IdoMcFly's post?

MC

---

### Post by az on 2005-03-15
I meant you wil not wipe out gnome.

---

### Post by mirtux on 2005-03-15
Thank you for your help.

Regards,
MC

---

### Post by IdoMcFly on 2005-03-15
I've managed to remove mozilla-firefox-locale-fr-fr by "sudo dpkg -r --force-depends" but at next update with aptitude, it have to be installed again :/ anyway to get rid of a dependency ?

---

### Post by IdoMcFly on 2005-03-16
[QUOTE=IdoMcFly]I've managed to remove mozilla-firefox-locale-fr-fr by "sudo dpkg -r --force-depends" but at next update with aptitude, it have to be installed again :/ anyway to get rid of a dependency ?[/QUOTE]
 ok forget it, I removed language-support-fr and manually keep installed the one I wanted to keep :)

---

