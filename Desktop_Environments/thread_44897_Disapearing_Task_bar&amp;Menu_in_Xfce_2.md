---
title: "Disapearing Task bar&amp;Menu in Xfce 2"
date: 2005-06-28
forum: Desktop Environments
---

### Post by Omnios on 2005-06-28
I have a slight problem with Xfce I turned off my right click menue. I was fiddling around with the XP like menu and the hole task bar dissapeared.

 Is there a was of deleating the desktop preferences or restoring the defaults?
I checked in the home directory and there isnt anything there.

---

### Post by Omnios on 2005-06-28
Correction its not the the bar that has the tasks that dissapears its the menu bar with the menues. Is there a term command to show it "xdesktop" dont work for this.
Basicly no menu bar or right click menu.

---

### Post by ranf on 2005-06-28
[QUOTE=Omnios]
 Is there a was of deleating the desktop preferences or restoring the defaults?
I checked in the home directory and there isnt anything there.[/QUOTE]

There is .config/ subdir in my home (at least with xfce 4.2.1)

---

### Post by skoal on 2005-06-28
[QUOTE=Omnios] Is there a was of deleating the desktop preferences or restoring the defaults?[/QUOTE]
yes, sir.  All you have to do is remove the ~/.cache folder.

rm -rf ~/.cache

should fix your problem.

/edit then log out and back in.

\\//_

---

