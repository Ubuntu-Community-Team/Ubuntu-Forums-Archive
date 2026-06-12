---
title: "Switch between KDE and Gnome - come on Gurus"
date: 2005-03-30
forum: Desktop Environments
---

### Post by vvu on 2005-03-30
I have Kubuntu and obviously it starts up KDE.  I am the main user, but I also have another user who uses this test machine that prefers Gnome.  I start up another X session but it defaults for this user to KDE.  How can I have a specific DM (Gnome) for this user?  I want KDM and the other user wants Gnome - and we are logged in at the same time (taking turns in test environment) - I am on Terminal 7 and he os on 8.   

Thanks   :smile:

---

### Post by lao_V on 2005-03-30
Have a look at the ~/.xsession files for both of you and you should be able to set which DM you want to run..for kde its startkde..not sure about gnome

---

### Post by Dracontopes on 2005-03-30
Interesting :)

I believe gnome was something like "gdm start" or... ? :D

---

### Post by lao_V on 2005-03-30
gdm start is to start the GNOME login manager (kdm start for kde) which only takes you to the chose login managar rather then actually load that DM for you

---

### Post by Julius on 2005-03-30
WIth GDM, when a user starts a DM that is not his/her default, it will ask the user if he/she wants that DM to be the new default.

---

### Post by freelsjd on 2005-03-30
One way to do this is to set up a .xinitrc file in your home directory and use "startx" or "xinit". This would have to be done outside the kdm or gdm front end which must be disabled. The user would just login to the console and then issue "startx" or "xinit". In the .xinitrc include all X-window initializations local to the X session. Include in this file "exec startkde" for kde or "exec gnome-session" for gnome.

---

### Post by apokryphos on 2005-03-30
Erm, no -- you can't have different display managers for different users as the display manager is not run from a particular user. It is from there that you log *into* a user. You can have a different *session* (i.e. kde/gnome) for each user, which is quite configurable from both GDM and KDM.

---

### Post by J. S. Jackson on 2005-03-31
I have been using GDM for both my KDE and Gnome sessions.  Does it matter which one you use?  GDM or KDM?

---

### Post by lao_V on 2005-03-31
It doesn't matter which one you use anymore because KDE 3.4 comes with 'skinnable' KDM which now looks and feels exactly like GDM. Can't tell the difference at all

---

### Post by J. S. Jackson on 2005-03-31
[QUOTE=lao_V]It doesn't matter which one you use anymore because KDE 3.4 comes with 'skinnable' KDM which now looks and feels exactly like GDM. Can't tell the difference at all[/QUOTE]

Ah great.  Thanks for that info.

---

