---
title: "Unity and gtk_key_theme"
date: 2011-11-02
forum: Desktop Environments
---

### Post by ryankask on 2011-11-02
I like to use emacs style keybindings in Gnome widgets. I just upgraded to 11.10 and I noticed that they no longer work (to be clear, I never used Unity in 11.04, so I don't know if it worked then).

I can see that "/desktop/gnome/interface/gtk_key_theme" (in gconf) is set to "Emacs".

Is it possible to make this work in Unity?

Best,
Ryan

---

### Post by ryankask on 2011-11-02
I'm going to answers my own question.

Unbeknownst to me, gconf has been replaced by dconf which is accessed through gsettings.

The fix was simple to run:

gsettings set org.gnome.desktop.interface gtk-key-theme "Emacs"

---

