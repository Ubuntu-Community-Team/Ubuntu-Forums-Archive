---
title: "Disable keyboard accelerators?"
date: 2009-06-03
forum: Desktop Environments
---

### Post by Fzang on 2009-06-03
Is it possible to disable keyboard accelerators in GNOME (or whatever controls it)?

---

### Post by jrib on 2009-06-18
> **Fzang said:**
> Is it possible to disable keyboard accelerators in GNOME (or whatever controls it)?

Add the following to your gtkrc (use ~/.gtkrc or ~/.gtkrc.mine if your ~/.gtkrc sources it) [1]:

```

gtk-enable-accels = 0
gtk-enable-mnemonics = 0

```

Also, for firefox, set the following to 0 in about:config [2]:

```

ui.key.generalAccessKey
ui.key.chromeAccess
ui.key.contentAccess 
ui.key.menuAccessKey

```

[1] [http://library.gnome.org/devel/gtk/stable/GtkSettings.html](http://library.gnome.org/devel/gtk/stable/GtkSettings.html)
[2] [http://kb.mozillazine.org/About:config_entries](http://kb.mozillazine.org/About:config_entries)

---

### Post by Fzang on 2009-06-19
Thanks a lot. It works :)

---

### Post by jrib on 2009-06-19
Yep, I have to disable it so the alt-* emacs keybindings for gtk text entries work right

---

### Post by erjoalgo on 2011-06-08
Dude, all you need to do is disable the menu bar on the terminal where you are using emacs.
*facepalm*

---

### Post by jrib on 2011-06-08
> **erjoalgo said:**
> Dude, all you need to do is disable the menu bar on the terminal where you are using emacs.
*facepalm*

no one is using emacs :)

---

