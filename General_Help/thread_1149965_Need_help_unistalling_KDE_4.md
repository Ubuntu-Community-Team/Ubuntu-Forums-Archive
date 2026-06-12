---
title: "Need help unistalling KDE 4"
date: 2009-05-05
forum: General Help
---

### Post by Tipped OuT on 2009-05-05
Fixed

---

### Post by Tipped OuT on 2009-05-05
Bump :(

---

### Post by Tipped OuT on 2009-05-05
bump

---

### Post by kay-man on 2009-05-05
Did you install kde packages or kubuntu?

You can try

sudo apt-get remove kde*

or 

sudo apt-get remove kubuntu*

Alternatively you can leave out the '*' and hit tab twice for command completion. That should show you if you have any of these packages still installed.

You might also try

sudo apt-get autoremove

to remove any packages that were automatically pulled in.

---

### Post by Tipped OuT on 2009-05-05
Thanks it worked :)

---

