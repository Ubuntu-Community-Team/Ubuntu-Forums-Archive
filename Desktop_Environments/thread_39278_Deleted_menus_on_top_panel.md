---
title: "Deleted menus on top panel"
date: 2005-06-04
forum: Desktop Environments
---

### Post by jer1ch0 on 2005-06-04
I was playing with my desktop and accidently deleted the three menus on the top panel - Applications, System and Places. 
How can I get them back?

---

### Post by flanker on 2005-06-05
To delete all your panel settings and restore the defaults.

log in, right click your desktop and choose open terminal, type;

rm -rf ~/.gconf/apps/panel/*

Then logout and back in again.

---

### Post by jer1ch0 on 2005-06-05
Thanks alot, but other circumstances forced a re-installation which solved the problem.

---

### Post by psychicdragon on 2005-06-05
Right click on panel > Add to Panel > Menu Bar

Just in case it goes missing or whatever again.

---

