---
title: "Access Samba from Root Nautilus"
date: 2007-05-10
forum: Desktop Environments
---

### Post by BadServo on 2007-05-10
This is proving to be a bit of a sticky issue.

It's not uncommon for me to launch a root instance of Nautilus by running "sudo nautilus" or su'ing into root and simply running "nautilus".  This works fine for local file management but not for Samba access.

For example... I can navigate to the samba share in user-level nautilus by typing "smb://mypc/share" into the location bar.  If I launch nautilus as root, however, I get an error stating that Nautilus cannot display the location and to try another viewer.

A more knowledgable linux user recommended I run "su -" to load the root profile and then launch Nautilus... but that give me an error stating "cannot load display".

Any advice is appreciated.

---

