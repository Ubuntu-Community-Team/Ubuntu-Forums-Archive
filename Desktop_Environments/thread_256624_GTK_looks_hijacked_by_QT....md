---
title: "GTK looks hijacked by QT..."
date: 2006-09-13
forum: Desktop Environments
---

### Post by Ramses de Norre on 2006-09-13
Hi,

I have currently both ubuntu-desktop and kubuntu-desktop installed and I use fluxbox as my main wm.
But recently I discovered a problem with my gtk apps, their themes and fonts etc. seem to be controlled by my settings in the gtk tab in kcontrol and don't seem to respond to anything I select in gnome-theme-manager or gnome-font-properties.. Gnome-settings-daemon is started when fluxbox is started and it's running.

I allready tried removing the gtk2-engines-gtk-qt package which removed the gtk tab in kcontrol but didn't let me change my gtk themes or fonts anymore.

Does anyone know how to get the gtk looks controlled by the native gnome apps again?

---

### Post by Lord Illidan on 2006-09-13
Perhaps you have to remove this too : gtk2-engines-qtpixmap

---

### Post by Ramses de Norre on 2006-09-13
I don't have that package installed..

---

### Post by ayoli on 2006-09-13
rm -rf ~/.gtkrc*

---

### Post by Ramses de Norre on 2006-09-13
Yeah that worked! I purged the gtk2-engines-gtk-qt package and then deleted all .gtkrc* stuff. That hosed gnome-settings-daemon and gdm and forced me to hard reboot but now everything works perfect.

I hope kde/qt will behave himself now ;)

---

### Post by ayoli on 2006-09-13
gnome theme settings are stored in gconf, but gtk settings from kde generates a .gtkrc-2.0 file that overrides gconf settings.

---

