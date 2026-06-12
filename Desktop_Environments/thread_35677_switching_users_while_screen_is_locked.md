---
title: "switching users while screen is locked?"
date: 2005-05-19
forum: Desktop Environments
---

### Post by graigsmith on 2005-05-19
is it possible to log in as a different user if my screen is locked?

i know you can open that new user thing, but how can someone use my computer when my screen is locked?

---

### Post by metallikop on 2005-05-19
[QUOTE=graigsmith]is it possible to log in as a different user if my screen is locked?

i know you can open that new user thing, but how can someone use my computer when my screen is locked?[/QUOTE]
 Currently there is no way to "switch users" as in windows, and if your screen is locked really the only way someone else could log in without knowing your password would be to switch to a vacent vterm (Ctrl+Alt+F1 through F6) and `sudo /etc/init.d/gdm restart`.  Naturally this user would have to be in /the sudoers file.  Edit your sudoers file with visudo (`sudo visudo`).

---

### Post by graigsmith on 2005-05-20
[QUOTE=metallikop]Currently there is no way to "switch users" as in windows, and if your screen is locked really the only way someone else could log in without knowing your password would be to switch to a vacent vterm (Ctrl+Alt+F1 through F6) and `sudo /etc/init.d/gdm restart`.  Naturally this user would have to be in /the sudoers file.  Edit your sudoers file with visudo (`sudo visudo`).[/QUOTE]
 is the only other way to reset the computer? 

i wish there was something that would start an instance of gnome login every time someone opened a new x session like  ctrl-alt-f8

is there a file that i can edit so that there can always be 2 gnome sessions running?

theres 6 terminal logins that are usable,  why not at least 2 gnome sessions?  i figure they dont do it cause it takes up some memory to do that, but as configurable as linux is, i would think the option is probably there somewhere, to start 2 gnome sessions.  one on alt-ctrl-f7  and one on f8.

---

### Post by graigsmith on 2005-05-20
oh wow i figured it out.  you have to edit the /etc/X11/gdm/gdm.conf file. and start 2 servers.

go down to the [services] section.

there will be 0=standard. followed by #1=standard.  just uncomment that to 1=standard. and 2 GDM's will start, one on f7 and one on f8 

:)

---

