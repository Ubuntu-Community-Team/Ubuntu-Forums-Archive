---
title: "Application starts twice at startup"
date: 2009-06-01
forum: Desktop Environments
---

### Post by blakescello on 2009-06-01
Before I upgraded to the latest Ubuntu, I had KeePassX installed and set to startup automatically on login. When I upgraded to 9.04, KeePassX continued to start up, but now I get two instances of the program instead of one. I tried editing the startup applications through the preferences menu, but there is only one entry for KeePassX. I uninstalled and then reinstalled the program, but I still get two instances of the program at startup. I've looked for documentation on manually editing the startup config file, but I can't figure out where it is.

---

### Post by mgmiller on 2009-06-02
Take a look in ~/.config/autostart and see if anything is duplicated in there.  This is where the startup config files that you create are kept.

---

