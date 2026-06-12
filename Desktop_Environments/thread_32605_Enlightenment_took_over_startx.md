---
title: "Enlightenment took over startx?"
date: 2005-05-08
forum: Desktop Environments
---

### Post by benplaut on 2005-05-08
in my quest for the perfect DE, i installed Enlightenment, then promptly uninstalled it (it is GUI, as in goo). however, when i need to restart X server, i...

log out

ctrl+alt+F1

login (CLI)

$ startx

__

and yet, it tries to start the non-existent Enlightenment, instead of the should-be-default GDM.

what config file do i need to edit?  :-|

---

### Post by tread on 2005-05-08
.Xsessions or .xinitrc in your home directory

---

### Post by benplaut on 2005-05-08
[QUOTE=tread].Xsessions or .xinitrc in your home directory[/QUOTE]

.xinitrc says:

# Enlightenment inserted Execution string here
exec /usr/bin/enlightenment

what should it say to execute GDM?

---

### Post by tread on 2005-05-08
Just remove that line, thats all the change you need do.

To enable the graphical greeter, 
System->Administration->Login Screen Setup.
Change local greeter to graphical greeter.

---

### Post by Ptero-4 on 2005-05-10
[QUOTE=tread]Just remove that line, thats all the change you need do.

To enable the graphical greeter, 
System->Administration->Login Screen Setup.
Change local greeter to graphical greeter.[/QUOTE]
 just remove .xinitrc and/or .Xsessions from your home folder and logout/login. It'll catch the system-wide settings which run gdm.

---

