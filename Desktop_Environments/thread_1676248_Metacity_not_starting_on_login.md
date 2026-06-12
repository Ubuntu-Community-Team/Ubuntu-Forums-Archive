---
title: "Metacity not starting on login"
date: 2011-01-26
forum: Desktop Environments
---

### Post by flyingboy on 2011-01-26
Hey,
   So I am relatively familiar with Ubuntu, but am afraid of what I have done, although I think it should be easily fixed.

I tried installing enlightenment 16 onto my computer. I didn't like it, and found out that I could simply uninstall it and issue a command to restart metacity. Well now when I login to my computer I have no window manager; I have my main menu and windows will open, but I cannot maximize, minimize, or close them. If I start terminal and type "metacity" it starts and I have my managers back (although I have my computer with compiz and Macbuntu so everything seems very rough).  Should I try a reconfig of compiz or metacity or a reinstall from synaptic? Any help would be greatly appreciated!

---

### Post by Krytarik on 2011-01-26
Check in Gconf if Metacity is enabled to run at startup:

- press Alt+F2
- enter gconf-editor
- browse down the path "/desktop/gnome/applications/window_manager"
- "/usr/bin/metacity" should be stated in both "current" and "default"
- the value for Compiz would be "/usr/bin/compiz"

---

### Post by flyingboy on 2011-01-27
yep. For some reason it seems to have returned to normal. Very bizarre. Thanks!

---

