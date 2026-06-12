---
title: "Substitute gmrun for gnome run dialog"
date: 2008-02-04
forum: Desktop Environments
---

### Post by CLI-Linux on 2008-02-04
Okay,

I googled this problem a week ago and found the answer, and then I reformatted my computer and now I can't find the solution.  Here's the problem:

I removed gnome-panel from the session since I'm running Avant Window Navigator with Compiz-Fusion.  Since gnome-panel is gone alt-f2 no longer does the run dialog, so i installed gmrun.  And, I think because Compiz is running, the Metacity global_key_bindings in gconf-editor don't work either.  So, I need to know how to bind gmrun to alt-f2 without doing it with the metacity global_key_bindings or the keyboard shortcuts in gnome.  I'm pretty sure it still has to do with settings in gconf-editor but I can't remember.

any ideas or links?

Thanks, guys.

---

### Post by ayoli on 2008-02-04
You may try compiz keybindings. Open compiz config (Menu Systeme > Preferences > Advanced Desktop Settings. If you dont have this run sudo apt-get install compizconfig-settings-manager).
Then go to "general", pick the tab "commands" in an empty line put "gmrun" (without quotes).
Then, still in "general", pick the tab "actions", go to "commands" enter a keybinding for the command line number that match the one you choose for gmrun.
Taht's all.

---

### Post by CLI-Linux on 2008-02-04
Thanks...I tried that twice, but I guess I forgot to turn off the alt+f2 binding in the keyboard shortcuts.  I turned it off this time, and it works.  :)

---

