---
title: "moving /home"
date: 2005-09-01
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-09-01
ok i put home on its own partition and altered fstab and nothing worked. changed a few things and nope. no permission to write to .gnome2 and .gnome2_private - changed permissions. nothing. set everything back where it was. nothing. 
altered all files to have all permissions for everyone. nothing (shouldn't have done that there was no undo). create a new user. same problems.

anyone any ideas. sorry for the crappy typing, i'm at a library and out of time :(

---

### Post by sumadartson on 2005-09-01
Hi,

Could you include your fstab and perhaps the relevant sections of ```
ls -aho ~
```?

Also, have you executed the chown and chmod commands recursively? That is for instance, ```
chown -R username directory
```

---

