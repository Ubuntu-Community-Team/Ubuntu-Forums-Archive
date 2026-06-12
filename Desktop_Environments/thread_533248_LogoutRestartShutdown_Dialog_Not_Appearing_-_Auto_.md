---
title: "Logout/Restart/Shutdown Dialog Not Appearing - Auto Logout"
date: 2007-08-23
forum: Desktop Environments
---

### Post by bunnyfly on 2007-08-23
Hello - the last couple days, when I click System-Quit or the little exit door on my panel, instead of offering me the "Shutdown/Logout/Suspend/Etc" dialog, it just immediately logs out.

Does anyone know how to get the dialog back? I've searched through Preferences-Sessions, many forums, gdm.conf, reinstalled gnome-panel, but can't find anything out. Please help!

---

### Post by fiuman on 2007-10-30
i have this problem too, upgraded by feisty to gutsy. Anyone can tell how to restore the previous behaviour?

---

### Post by aztektum on 2007-11-01
All I can think of is ...

System >> Administration >> Login Window

On the Local tab, make sure the "Show Action Buttons" box is checked. This fixed my problem with MISSING buttons on the default shutdown dialog, but I still saw it, so YMMV

---

### Post by boogaone on 2008-01-31
Not sure if you have found a solution but this worked for me:
Go into the configuration editor and in the side pane APPS>GNOME-SESSION>OPTIONS make sure "logout_option"  is left blank and "logout_prompt" is ticked.

---

