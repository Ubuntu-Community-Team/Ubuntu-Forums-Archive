---
title: "gnome-shell: how to reorder dash icons without dragging [solved]"
date: 2015-04-07
forum: Desktop Environments
---

### Post by geoffmen on 2015-04-07
gnome-shell systematically crashes when I try to move the launchers. I can probably edit some files somewhere to reorder them... where?

---

### Post by deadflowr on 2015-04-08
You can use dconf-editor (or gsettings from cli)
look in the sections org >> gnome >> shell >> favorite-apps.
The list should be in order from top to bottom.
Adjust how you want, be careful out there.

gsettings command would be:

To see what the layout currently is:
```
gsettings get org.gnome.shell favorite-apps
```
which should show something like
```
['firefox.desktop', 'thunderbird.desktop', 'org.gnome.Nautilus.desktop']
```
follow the output as a guide when readjusting.

To change the layout use the set option like so:
```
gsettings set org.gnome.shell favorite-apps ['some-app.desktop', 'another-app.desktop', 'another-app.desktop']
```
I think common sense dictates these will be ordered top to bottom in the order listed.

If all fails try:
```
gsettings reset org.gnome.shell favorite-apps
```
will, or at least should, reset it to the default.

Personally, I'd install dconf editor and do it graphically.

---

### Post by kerry_s on 2015-04-08
> **geoffmen said:**
> gnome-shell systematically crashes when I try to move the launchers. I can probably edit some files somewhere to reorder them... where?

what version ?

i'm using the beta 15 ubuntu gnome, it's been solid for me.

you could try changing to "dash to dock" extension which is what i use, that way you could tweak to your liking.

---

