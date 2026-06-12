---
title: "Lucid still has old Karmic login screen"
date: 2010-05-15
forum: Desktop Environments
---

### Post by matthorr on 2010-05-15
My login screen is still the old one from Karmic (brown) after updating to Lucid.  How do I update to the new purple look?

---

### Post by vilain_mamuth on 2010-05-27
you are not alone....

i upgraded 2 PCs, one is ok, the other not.:(

any news since your post?

---

### Post by vilain_mamuth on 2010-05-27
removing /var/lib/gdm/.gconf folder was successful for me

---

### Post by matthorr on 2010-05-27
Thanks, that worked for me.

Here is the command (in a terminal window):
sudo rm -r /var/lib/gdm/.gonf

The new "purple" screen appeared on my next login.  It's uglier than the one from Karmic, but at least it matches my desktop.

---

