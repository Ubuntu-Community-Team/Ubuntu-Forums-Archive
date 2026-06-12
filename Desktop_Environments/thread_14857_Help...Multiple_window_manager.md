---
title: "Help...Multiple window manager"
date: 2005-02-10
forum: Desktop Environments
---

### Post by lao_V on 2005-02-10
Hi, 
 
 I recently installed Afterstep from synaptic. How do I start using it?
 
 It doesn't appear in the options on the Login Manager and when I type in afterstep in terminal it says another window manager is already running.
 
 Can anyone help?

---

### Post by mendicant on 2005-02-10
You can check if you have .gnome2/session.  If not, copy /usr/share/gnome/default.session to .gnome2/session, then change the gnome-wm command to have --default-wm afterstep.

---

### Post by lao_V on 2005-02-10
[QUOTE=mendicant]You can check if you have .gnome2/session.  If not, copy /usr/share/gnome/default.session to .gnome2/session, then change the gnome-wm command to have --default-wm afterstep.[/QUOTE]
 Thanks mendicant, I'll try that when I get home.

---

