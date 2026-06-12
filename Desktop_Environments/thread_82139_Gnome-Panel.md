---
title: "Gnome-Panel"
date: 2005-10-26
forum: Desktop Environments
---

### Post by djur on 2005-10-26
After installing breezy gnome-panel no longer loads.  I have reinstalled xorg, gnome-panel and gnome-panel data to no avail.  How can I add gnome-panel to the config file so that it loads at gnome start-up?

---

### Post by aysiu on 2005-10-26
Is it that you can't turn the gnome-panel on *at all*, or that it won't turn on at startup?

---

### Post by endersshadow on 2005-10-26
If it's the case where it won't *load*, go to the System menu to Preferences and select Sessions.  Hit the Startup Programs.  Add gnome-panel.  Done.

Now, if it won't *start at all*, we've got more of a problem on our hands.

---

### Post by djur on 2005-10-29
It will run.  I made a script to run it..  but I'd prefer it be loaded before everything else when gnome starts up.

---

### Post by bvc on 2005-10-29
once you have it running and have your desktop the way you want it when you login, hit Alt+F2, and type;
gnome-session-save
and click the run button. Oh, and then remove the script.

---

