---
title: "Gnome/GTK apps freezing up - accesibility configuration issue?"
date: 2007-06-05
forum: Desktop Environments
---

### Post by rgould on 2007-06-05
Using KDM, when I log into Gnome, widgets freeze completely.
* Works fine if logged in as a different user (so it is my settings that are causing it)
* running Ubuntu 6.06 - don't want to upgrade just yet

If I log into Gnome, everything will start okay. But if I open a GTK application, or open the main Gnome menu, all of the GTK widgets stop responding (and do not repaint themselves). I must then restart KDM to use the computer again. When I had GDM running, the login textbox at the GDM prompt would also seize up (that's why I am running KDM).

After Gnome seizes up, I can get GTK apps to run in KDE after executing /etc/init.d/kdm stop, and killing all Gnome processes that locked up (gnome-pty-helper, nautilus, tilda, gnome-terminal, etc.). I then start up KDM and log-in to KDE and GTK apps run okay.

Right before this started, I was playing around in the Gnome accessibility options. None of the settings I were playing with should have persisted though, as I disabled them when I was done.

I have checked all of the logs that I am aware of (which logs should I be checking?) and there is nothing
interesting there. Does anyone have any tips? I'd like to fix this myself, but I need a kick in the right direction.

---

