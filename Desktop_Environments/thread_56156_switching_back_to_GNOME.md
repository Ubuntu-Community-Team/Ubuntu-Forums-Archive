---
title: "switching back to GNOME"
date: 2005-08-11
forum: Desktop Environments
---

### Post by nsa_767 on 2005-08-11
Hi there,

I'm relatively new to linux (so be gentle).... I installed the normal Ubuntu (Hoary) without any problems, downloaded Kyle (KDE LaTex editor) and found that it didn't run too nicely through GNOME. So I installed KUbuntu, to get the KDE.

It installed without any problems, and it asked me which windowmanager I want to make my default. Not exactly understanding, I chose KWM (I think...) as the default...

However, I'd like to change back to having GNOME as the default WM for all users, but I'd still like to keep KDE there for in case I need to use Kyle.

How do I set GNOME as the default WM for the whole system, without uninstalling KDE.

---

### Post by SGC on 2005-08-11
-

---

### Post by varunus on 2005-08-11
Open up a terminal and type "sudo dpkg-reconfigure gdm".  Then pick gdm as your default login manager.  You'll now be using the GNOME login manager next time you log out.  Then, just pick GNOME on your next login...

---

### Post by Ptero-4 on 2005-08-11
[QUOTE=varunus]Open up a terminal and type "sudo dpkg-reconfigure gdm".  Then pick gdm as your default login manager.  You'll now be using the GNOME login manager next time you log out.  Then, just pick GNOME on your next login...[/QUOTE]
 Or logout and pick GNOME from KDE login manager, kdm supports setting other WM's as default instead of KDE.

---

### Post by nsa_767 on 2005-08-12
Thanx!!!

[QUOTE=varunus]Open up a terminal and type "sudo dpkg-reconfigure gdm".  Then pick gdm as your default login manager.  You'll now be using the GNOME login manager next time you log out.  Then, just pick GNOME on your next login...[/QUOTE]

That worked... Exactly what I needed.... Thank you again!

---

### Post by elgx on 2005-08-23
er... i just signed in here.
well, i had exactly the same trouble, and tried this:

sudo dpkg-reconfigure gdm

but didn't work.
i restarted the session and the login screen was that of Kubuntu...
of course after logging in the session was gnome (i use it virtually everyday, and kdm only if having problems with gnome)... but is the login screen that i want to change.

sorry, my english isn't that beautiful ^^
byez!


EDIT: i have just made a mistake with the CTRL+ALT+F* combination, I think. because now only in the F8 screen i recognize the theme-icons-windowBorder-controlTheme status i had. in other screens (F7, F9) i have the window border theme but not controls and icons... HELP! how can I set THIS ONE (F8) as default? how can i solve the above problem with the login manager?

---

