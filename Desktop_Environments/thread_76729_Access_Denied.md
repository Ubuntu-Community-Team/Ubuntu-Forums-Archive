---
title: "Access Denied"
date: 2005-10-15
forum: Desktop Environments
---

### Post by S.nazari on 2005-10-15
Guys I'm using KDE and I have found that I can' t delete my files form my computer desktop  or anyother place in my space for that matter /home/me, is locked out to me I don't know what to do.
I can save and read form the space but I can't delete with out sudo form the terminal. This has only recently happened I upgraded to the breezy.

---

### Post by agm642 on 2005-10-15
Try "sudo konqueror" and change their permissions.

---

### Post by Xiata on 2005-10-15
In a console:
sudo chown -R **yourusername** /home/**yourusername**
sudo chgrp -R **yourusername** /home/**yourusername**
sudo chmod -R /home/**yourusername** u+rw
sudo chmod -R /home/**yourusername** g+rw

Replace all instances of **yourusername** with your login name,
example if your login is joebob: sudo chgrp -R joebob /home/joebob

---

