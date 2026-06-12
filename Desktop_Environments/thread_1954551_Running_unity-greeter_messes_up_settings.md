---
title: "Running unity-greeter messes up settings"
date: 2012-04-08
forum: Desktop Environments
---

### Post by dr_saaron on 2012-04-08
Reading another thread, I stupidly run the command unity-greeter from the terminal.  And now my settings are all messed up.  The icon theme is changed, the unity bar looks different, all the program seem to be running gtk2 or something weird like that.  I can't figure out what settings got updated and so can't revert it.  Any ideas?

---

### Post by dr_saaron on 2012-04-08
I was able to work around this by deleting my ~/.config/dconf/user file and restarting.  I lost some settings like desktop background and icons on the launcher, but I can put those back.  Hope I didn't lose anything else.

---

