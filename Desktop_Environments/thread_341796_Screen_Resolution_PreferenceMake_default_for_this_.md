---
title: "Screen Resolution Preference:Make default for this computer: undo?"
date: 2007-01-19
forum: Desktop Environments
---

### Post by arthur_lean on 2007-01-19
Hi, i'am using nomachine nx, and normally when you logon, then screen will fit the resolution you choose for the connection.
but then after using the option Make default for this computer on the local login, the setting is forced onto nx remote login as well](*,) .

so if someone could kindly point out which config file the setting is applied to and be removed.
ps. i've looked at xorg.config file. the Display section seems to look fine. :-k 


thxs in advance.

---

### Post by BionicSeahorse on 2007-03-19
I was able to fix this by deleting the ```
~/.gconf/desktop/gnome/screen/default/0/%gconf.xml
``` file inside of your home folder and restarting GNOME. If you want to do this from inside X, you will need to show hidden files (inside the "View" menu)

Hope that helps! :)

---

