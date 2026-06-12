---
title: "Desktop completely broken, help"
date: 2011-12-03
forum: Desktop Environments
---

### Post by SchneiderIS on 2011-12-03
So fari have been completely frustrated with 11.10.  At this point it is totally useless because I can't do anything with the desktop.  I don't have the menu along the top I don't have any menus at all!   The desktop is slowly disabling what functionality I do have as I cannot move the windows that are up.  I have a big X as my mouse.

Any ideas on how to restore the desktop?

---

### Post by bluexrider on 2011-12-03
drop back to the classic mode

sudo apt-get install gnome-panel

log out, choose classic from the drop-down menu, log in

---

### Post by oldtimer7777 on 2011-12-03
> **SchneiderIS said:**
> So fari have been completely frustrated with 11.10.  At this point it is totally useless because I can't do anything with the desktop.  I don't have the menu along the top I don't have any menus at all!   The desktop is slowly disabling what functionality I do have as I cannot move the windows that are up.  I have a big X as my mouse.

Any ideas on how to restore the desktop?

You can reinstall ubuntu-desktop package to pull everything that has been messed up.

In terminal:

sudo apt-get install ubuntu-desktop

---

### Post by SchneiderIS on 2011-12-03
Thanks for the quick reply.

Sadly, no success.  After a very long install it did nothing but add a virtual keyboard.

---

### Post by raja.genupula on 2011-12-03
```
sudo apt-get install --resinstall ubuntu-desktop
```

---

### Post by SchneiderIS on 2011-12-04
Nope.  All that did in the end was add Orca to the useless interface.  

At this point I am reinstalling from disk.

---

