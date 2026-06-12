---
title: "Highlight color in GDM"
date: 2005-06-14
forum: Desktop Environments
---

### Post by ChinaCatJones on 2005-06-14
I have recently switched my login screen under gdm to a user list one with a crystal look.  However, the users are highlighted with a color suitable for the human theme.  How do I change this color to something more appealing for the current theme?

Thanks

---

### Post by Alexander Kirillov on 2005-06-14
[QUOTE=ChinaCatJones]I have recently switched my login screen under gdm to a user list one with a crystal look.  However, the users are highlighted with a color suitable for the human theme.  How do I change this color to something more appealing for the current theme?

Thanks[/QUOTE]
 Edit file (using sudo)
/etc/X11/gdm/gdm.conf
Uncomment line 
GtkTheme=
and use there the GTK theme you like. E.g.: 
GtkTheme=Mist
Save file. Logout, restart X by pressing ctrl-alt-backspace

---

### Post by ChinaCatJones on 2005-06-14
Thanks.  Worked great!

---

