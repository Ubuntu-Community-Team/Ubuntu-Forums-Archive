---
title: "Power Management pop up on login"
date: 2009-04-02
forum: General Help
---

### Post by my-cool on 2009-04-02
I was playing around with the start up sessions and decided to remove Power Management, thinking that it was for laptops, then i noticed that when u remove it, the Shut Down and Restart buttons disappear from the Fast-switch-user, now that i'v added Power Management back to sessions, whenever i login, the Power Management window pops up, is there any way to disable that from happening??

---

### Post by my-cool on 2009-04-02
bump

---

### Post by ptn107 on 2009-04-02
Your entry in System -> Preferences -> Sessions (or 'Startup Applications' if your using jaunty) should be as follows.

Name: Power Manager
Command: gnome-power-manager
Comment: Power management daemon

---

### Post by my-cool on 2009-04-03
ah awesome that fixed it,
i had "Command: gnome-power-preferences" instead of "Command: gnome-power-manager"

thanx for the help

---

### Post by ptn107 on 2009-04-03
no problem

---

