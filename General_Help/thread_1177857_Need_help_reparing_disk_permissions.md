---
title: "Need help reparing disk permissions"
date: 2009-06-03
forum: General Help
---

### Post by Nathannb on 2009-06-03
im trying to get all the files off my hard drive from my old ibook but it says i cant because i dont have permission and when i goto properties and change the permissions it says "you are not the owner, you cannot change these permissions"
is there anyway i can get around this
the file system is corrupt so it will mount but not appear in finder on my MB
im trying to find a alternative to disk warrior or similar stuff

please help

---

### Post by deepclutch on 2009-06-03
sudo chmod -R 755 to the directories may fix hopefully.but the better option is ,you invoke nautilus file manager as root.
press alt+f2 and run "gksudo -u root nautilus" or for kde fan "kdesu konqueror" and change permissions.

---

### Post by Nathannb on 2009-06-03
wow that was fast
and it worked
thank you sooo much
big help :]

---

