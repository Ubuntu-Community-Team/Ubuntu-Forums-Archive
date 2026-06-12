---
title: "Unable to authenticate/execute the action (code4)  - Need Help"
date: 2010-11-21
forum: Desktop Environments
---

### Post by wiseguy12851 on 2010-11-21
I wanted to change the KDM login themes and have been installing themes through Login Screen Settings but the installed themes never showed up as an option to select so I wanted to manually install a theme

Upon system restart something had crashed, I didn't note what it was as my system was restarting and pen/paper wasn't available, the login theme couldn't load so I manually loaded KDE through the command prompt.

I was going to reset my manual changes through the Login Screen Settings but it couldn't apply the changes. The exact error message was:

Title:  Error-System Settings
Msg:   Unable to authenticate/execute the action:  (code 4)

This pops up instead of asking for credentials to change system settings. Now I can log into other stuff as root such as Konsole > gksudo dolphin but I haven't tested everything as to success or not.

EDIT:
Additional discovered information:
Desktop effects and games are extremely slow, KDE gave message that Desktop effects were actually automatically disabled due to lagging speed, games are so slow they eventually freeze up and won't close.
     Hope that helps

---

### Post by obeliksz on 2011-11-04
The same for me. Help!

---

### Post by kunir on 2012-01-26
Installing polkit-kde-1 package solved the problem for me.

---

