---
title: "can't find gnome-session config file"
date: 2011-12-06
forum: Desktop Environments
---

### Post by errrn on 2011-12-06
Hello everyone,

Tired of unity I decided to try a few alternatives, and before deciding to go for cairo dock, I played around my gnome classic setup, and I managed to mess it up some how.

I deleted the bottom panel and edited the top panel. And I'm trying to set the auto hide time via gconf-editor, but there's no way I can find the session setup file.

I went every imaginable folder, and I even deleted the .gnome2 folder.
The strange thing is that the editing I did on the top panel, stay. But I have no idea where are they saved.

any ideas?
cheers

---

### Post by stinkeye on 2011-12-06
Possibly dconf-editor (need dconf-tools)
org.gnome.gnome-panel

---

### Post by errrn on 2011-12-06
dconf-tools was the thing.

thank you

---

