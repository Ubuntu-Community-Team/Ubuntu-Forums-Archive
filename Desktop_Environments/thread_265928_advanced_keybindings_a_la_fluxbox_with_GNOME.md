---
title: "advanced keybindings a la fluxbox with GNOME?"
date: 2006-09-26
forum: Desktop Environments
---

### Post by heisters on 2006-09-26
Hi all,

I'm wondering if there's any way to get Gnome keybindings to behave like Fluxbox's. The basic features I'm missing are chaining (like emacs, eg. Ctrl-W A), launching arbitrary commands (the closest I can see is opening a run dialog), and window management (resizing/moving windows with the keyboard).

The best solution I see so far is actually to replace Metacity with Openbox, which has keybindings similar to Fluxbox. However, I'm afraid this might conflict with the standard Gnome keybinding manager, as well as disabling the prettiness of Metacity and perhaps Compiz.

Is there any way to extend the default GNOME keybinder? Does it have settings I've completely overlooked? Might Compiz have a more advanced keybinding setup? I'd settle for the latter two features if I couldn't get chaining working.

Thanks!

---

### Post by ayoli on 2006-09-26
open gconf-editor (under menu system tools or type in run dialog: gconf-editor) when you're in go in apps/metacity/keybindings_command edit the command you want, then go in apps/metacity/global_keybindings and assign a shorvut for each command you have entered before.
(see screenshots)
same can be done in compiz using csm.

---

### Post by heisters on 2006-09-27
Slick! I always forget that gconf can configure so much more than what shows up in the default preferences apps; this stuff doesn't show up in the keybinding preference. It'd be nice if there was a link in the main preference app like "advanced keybinding settings". Combining this with wmctrl (which I just found) should get me everything I need, while remaining window manager agnostic.

---

