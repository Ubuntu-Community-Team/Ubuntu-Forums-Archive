---
title: "Is there a way to default autorun items for new users?"
date: 2011-09-16
forum: Desktop Environments
---

### Post by jimerman on 2011-09-16
Windows has a default profile, so if I add startup items there, then the first time a user logs in he will get the default copied.

There has to be a way to do the same with Ubuntu.  I created a startup item in the Administrator preferences, and I can copy that to other users' directories.  However, I want to have that as a default in case a new user logs in.

I found my startup items in:

~/.config/autostart/

But if I go to /home, there is no default folder.

---

### Post by sanderd17 on 2011-09-16
Normally, the /etc/profile script is executed at each login (so also a non-GUI login if you use that).

For the GUI-only logins, you need to copy the ~/.config/autostart/ directory.

---

### Post by Lisiano on 2011-09-16
EDIT: Just add the files from ~/.config/autostart/ to /etc/skel/.config/autostart/

---

