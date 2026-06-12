---
title: "Adding user - &quot;home directory already exists&quot;"
date: 2009-05-17
forum: General Help
---

### Post by hackapelite on 2009-05-17
Well, I just finished installing 9.04. I created a partition for '/home', and I also created one for '/home/family/backups' on a different drive (as the name implies, it's basically a place for my family to back up their stuff). However, when I try creating a profile for them, specifying the home dir as '/home/family', it comes up with the error message "Home directory already exists". So, how can I make it use the existing /home/family folder?

---

### Post by dcstar on 2009-05-17
> **hackapelite said:**
> Well, I just finished installing 9.04. I created a partition for '/home', and I also created one for '/home/family/backups' on a different drive (as the name implies, it's basically a place for my family to back up their stuff). However, when I try creating a profile for them, specifying the home dir as '/home/family', it comes up with the error message "Home directory already exists". So, how can I make it use the existing /home/family folder?

What do you expect?, you should **not** manually create any folders in the /home tree, it is there for the system to create folders when new accounts are created.

Delete anything you created and let the system do the job it expects it is supposed to do.

---

### Post by hackapelite on 2009-05-17
The problem is fixed now. However, I could *not* delete the folder, because it was a mount point for a partition I made.

Also, now that we're at it... since this (apparently) is a rather unorthodox approach, what would be the "proper" way of having an user's home folder on a separate partition?

---

