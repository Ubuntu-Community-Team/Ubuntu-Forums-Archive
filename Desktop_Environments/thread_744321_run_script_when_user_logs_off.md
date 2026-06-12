---
title: "run script when user logs off"
date: 2008-04-03
forum: Desktop Environments
---

### Post by Greslore on 2008-04-03
I need to use a script that would delete the user's home dir upon them logging out.  What file would run a script everytime a user logs out?

---

### Post by Oldsoldier2003 on 2008-04-03
> **Greslore said:**
> I need to use a script that would delete the user's home dir upon them logging out.  What file would run a script everytime a user logs out?

Assuming you are using gnome :edit the file  /etc/gdm/PostSession/Default

---

### Post by Greslore on 2008-04-03
> **Oldsoldier2003 said:**
> Assuming you are using gnome :edit the file  /etc/gdm/PostSession/Default

This would be for a machine that would have KDE, GNOME, and also SSH logins available to the users. :)

---

### Post by nemilar on 2008-04-03
If it's a bash shell, you can use ~/.bash_logout

Only works for login shells, though.

---

