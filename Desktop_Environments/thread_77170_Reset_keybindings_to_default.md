---
title: "Reset keybindings to default?"
date: 2005-10-16
forum: Desktop Environments
---

### Post by stoffe on 2005-10-16
Boy, do I feel silly. :)

I was playing with System->Prefereces->Keyboard Shortcuts to test something out. Just to try a thing, I set the 'n' key to the action, and now, well... I have no 'n' key anymore.

Tried Googling and browsing Yelp, but no mention on how to restore the default key setup or even better, reverting one single key.

Would be extremely happy for some advice here. :)

Additionally, this seems to me a pretty dangerous bug, especially since there seems to be no easy way to revert such a mistake. There was no warning or even advice either. (Aware that it's a Gnome issue, but is it a known one?)

(Pasting in 'n' everywhere to make this text readable... tedious! :rolleyes:)

---

### Post by yage on 2005-10-16
Just go back to where you did this and click on the line with your 'n' entry. You will be able to set somethin else as a shortcut key... Just press the key og combo you wish to use.. Alt+F5 or something else for that matter

---

### Post by stoffe on 2005-10-16
[QUOTE=yage]Just go back to where you did this and click on the line with your 'n' entry. You will be able to set somethin else as a shortcut key... Just press the key og combo you wish to use.. Alt+F5 or something else for that matter[/QUOTE]
Already did that, doesn't help. The key seems permanently unbound...

---

### Post by yage on 2005-10-16
What if you try to edit the file by hand?
```
gedit /home/username/.gconf/apps/gnome_settings_daemon/keybindings/%gconf.xml
```

---

### Post by stoffe on 2005-10-16
Nothing related in that file, or in GCONF as it doesn't list non-defaults. However, it seems like a restart of X finally solved it.

Bit of a stumper and I would really hate to see this happen to someone more prone to panic. :) Seems like a dangerous design...

---

### Post by yage on 2005-10-16
Good thing the restart solved it.
And i couldn't agree more :???:

---

